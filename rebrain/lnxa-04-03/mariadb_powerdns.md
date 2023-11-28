# mariadb_powerdns

## install mariadb

```
sudo apt install mariadb-server -y
```

> secure installation

```
sudo mysql_secure_installation
```

> connect to the db

```
sudo mysql -u root
```

> create user with granted all privilegies

```
MariaDB [(none)]> GRANT ALL PRIVILEGES ON *.* TO 'mashka'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
exit
```

> check the status

```
systemctl status mysql
```

> change configuration of maria

```
sudo vim /etc/mysql/mariadb.conf.d/50-server.cnf

query_cache_size        = 256M
max_connections         = 200
wait_timeout            = 60
interactive_timeout     = 60
innodb_file_per_table   = ON
skip-name-resolve
slow_query_log          = 1
```

> create the db for powerdb

```
vim params.txt

CREATE DATABASE powerdns character set utf8;
GRANT ALL ON powerdns.* TO 'mashka'@'%' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
USE powerdns;
CREATE TABLE domains (
  id                    INT AUTO_INCREMENT,
  name                  VARCHAR(255) NOT NULL,
  master                VARCHAR(128) DEFAULT NULL,
  last_check            INT DEFAULT NULL,
  type                  VARCHAR(8) NOT NULL,
  notified_serial       INT UNSIGNED DEFAULT NULL,
  account               VARCHAR(40) CHARACTER SET 'utf8' DEFAULT NULL,
  options               VARCHAR(64000) DEFAULT NULL,
  catalog               VARCHAR(255) DEFAULT NULL,
  PRIMARY KEY (id)
) Engine=InnoDB CHARACTER SET 'latin1';

CREATE UNIQUE INDEX name_index ON domains(name);
CREATE INDEX catalog_idx ON domains(catalog);


CREATE TABLE records (
  id                    BIGINT AUTO_INCREMENT,
  domain_id             INT DEFAULT NULL,
  name                  VARCHAR(255) DEFAULT NULL,
  type                  VARCHAR(10) DEFAULT NULL,
  content               VARCHAR(64000) DEFAULT NULL,
  ttl                   INT DEFAULT NULL,
  prio                  INT DEFAULT NULL,
  disabled              TINYINT(1) DEFAULT 0,
  ordername             VARCHAR(255) BINARY DEFAULT NULL,
  auth                  TINYINT(1) DEFAULT 1,
  PRIMARY KEY (id)
) Engine=InnoDB CHARACTER SET 'latin1';

CREATE INDEX nametype_index ON records(name,type);
CREATE INDEX domain_id ON records(domain_id);
CREATE INDEX ordername ON records (ordername);


CREATE TABLE supermasters (
  ip                    VARCHAR(64) NOT NULL,
  nameserver            VARCHAR(255) NOT NULL,
  account               VARCHAR(40) CHARACTER SET 'utf8' NOT NULL,
  PRIMARY KEY (ip, nameserver)
) Engine=InnoDB CHARACTER SET 'latin1';


CREATE TABLE comments (
  id                    INT AUTO_INCREMENT,
  domain_id             INT NOT NULL,
  name                  VARCHAR(255) NOT NULL,
  type                  VARCHAR(10) NOT NULL,
  modified_at           INT NOT NULL,
  account               VARCHAR(40) CHARACTER SET 'utf8' DEFAULT NULL,
  comment               TEXT CHARACTER SET 'utf8' NOT NULL,
  PRIMARY KEY (id)
) Engine=InnoDB CHARACTER SET 'latin1';

CREATE INDEX comments_name_type_idx ON comments (name, type);
CREATE INDEX comments_order_idx ON comments (domain_id, modified_at);


CREATE TABLE domainmetadata (
  id                    INT AUTO_INCREMENT,
  domain_id             INT NOT NULL,
  kind                  VARCHAR(32),
  content               TEXT,
  PRIMARY KEY (id)
) Engine=InnoDB CHARACTER SET 'latin1';

CREATE INDEX domainmetadata_idx ON domainmetadata (domain_id, kind);


CREATE TABLE cryptokeys (
  id                    INT AUTO_INCREMENT,
  domain_id             INT NOT NULL,
  flags                 INT NOT NULL,
  active                BOOL,
  published             BOOL DEFAULT 1,
  content               TEXT,
  PRIMARY KEY(id)
) Engine=InnoDB CHARACTER SET 'latin1';

CREATE INDEX domainidindex ON cryptokeys(domain_id);


CREATE TABLE tsigkeys (
  id                    INT AUTO_INCREMENT,
  name                  VARCHAR(255),
  algorithm             VARCHAR(50),
  secret                VARCHAR(255),
  PRIMARY KEY (id)
) Engine=InnoDB CHARACTER SET 'latin1';

CREATE UNIQUE INDEX namealgoindex ON tsigkeys(name, algorithm);

```

```
sudo mysql -u root < params.txt
```

```
mysql -u mashka -p
mysql -u mashka -p -D powerdns

MariaDB [(none)]> use powerdns;
MariaDB [(powerdns)]> show tables;
```

> disable resolved

```
sudo systemctl disable systemd-resolved
sudo systemctl stop systemd-resolved
ls -lh /etc/resolv.conf 
sudo unlink /etc/resolv.conf
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
```

> install powerdns

```
sudo apt install -y \
pdns-server \
pdns-backend-mysql \
pdns-tools
```

> create new config file

```
sudo vim /etc/powerdns/pdns.d/mysql.conf

# MySQL Configuration
# Launch gmysql backend
launch+=gmysql
# gmysql parameters
gmysql-host=localhost
gmysql-dbname=powerdns
gmysql-user=mashka
gmysql-password=password
gmysql-dnssec=yes
```

## install powerdns-admin

```
sudo apt install python3-dev
```

## grep uncommented and empty lines in linux

```
sudo cat /etc/powerdns/pdns.conf | grep -v -e "^#" -e "^$"
sudo cat /etc/powerdns/pdns.conf | egrep '^[^#]'
sudo cat /etc/powerdns/pdns.conf | egrep '^[[:blank:]]*[^[:blank:]#]'
```

[link](https://kifarunix.com/easily-install-and-setup-powerdns-admin-on-ubuntu-20-04/)

[lin](https://kifarunix.com/easily-install-and-setup-powerdns-on-ubuntu-20-04/)

[flask](https://computingforgeeks.com/install-powerdns-and-powerdns-admin-on-ubuntu/)
