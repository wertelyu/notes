### 1. Installing mariadb

```
sudo apt install mariadb-server -y
```

### 2. Make sure InnoDB File-per-table is enabled

```
mysql --help --verbose
```

### 3. `query_cahe_size`

```
query_cache_size        = 256M
```

### 4. Enable logging for queries longer than 1 sec

```
slow_query_log_file    = /var/log/mysql/mysql-slow.log
long_query_time        = 1.0
```

### 5. `max_connections`

```
max_connections        = 200
```

### 6. `tmp_tabel_size`

```
tmp_table_size         = 134217728
```

### 7. timeouts

```
wait_timeout           = 60
interactive_timeout    = 60
```

### 8. Innodb File-per-table

```
innodb_file_per_table  = ON
```

### 9. Skip reverse DNS lookup of clients

```
skip-name-resolve
```

### 10. peak memory consumption


[calc](https://www.mysqlcalculator.com/)

[reference](https://superuser.com/questions/1411800/mysql-maria-memory-calculation-usage-creep)

```
SELECT ( @@key_buffer_size
+ @@query_cache_size
+ @@innodb_buffer_pool_size
+ @@innodb_log_buffer_size
+ @@max_connections * ( @@read_buffer_size
+ @@read_rnd_buffer_size
+ @@sort_buffer_size
+ @@join_buffer_size
+ @@binlog_cache_size
+ @@thread_stack
+ @@tmp_table_size )
) / (1024 * 1024 * 1024) AS MAX_MEMORY_GB;
```

---

innodb_buffer_pool_size
sort_cache


