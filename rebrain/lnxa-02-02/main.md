### 1. install postgresql

```
sudo apt install postgresql -y
```

```
pg_ctl reload
```

### 2. login by postgres username

```
sudo -u postgres -i
createdb mydb
dropdb mydb
```

```
psql mydb
select version();
\h # to get help
\q # to get out
```

Two dashes (“--”) introduce comments. Whatever follows them is ignored up to the end of the line.

SQL is case insensitive about key words

### 3. users

```
SELECT * FROM pg_catalog.pg_user;
\du
```

### 4. create sequence

```
CREATE SEQUENCE serial AS integer;
SELECT nextval('serial');
DROP SEQUENCE serial;

CREATE TABLE tasks (
    id task_id;
    name varchar(64));

INSERT INTO tasks (name) VALUES ('hello_first');
INSERT INTO tasks (name) VALUES ('hello_second');

SELECT * FROM tasks;
```


flooding in india
athmosphere green affect
aibergs meltin
see level arising
show everyone the resalt

drpugts

air - rising seas

i doubt it 


fossil coligues
get distracted

to keep in mind

