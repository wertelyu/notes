# how to deploy django app

### install all requared dependenses

```bash
sudo apt-get install -y \
python3-pip \
python3-dev \
libpq-dev \
postgresql \
postgresql-contrib \
nginx
```
```bash
sudo atp install python3.x-venv -y
```

### access to the psql

```bash
sudo -u postgres -i
createdb mydb
psql mydb
```

```bash
CREATE USER mydbuser WITH PASSWORD 'password';
ALTER ROLE mydbuser SET client_encoding TO 'utf8';
ALTER ROLE mydbuser SET default_transaction_isolation TO 'read committed';
ALTER ROLE mydbuser SET timezone TO 'UTC';
GRANT ALL PRIVILEGES ON DATABASE mydb TO mydbuser;
\q - quit
\l - The output shows a list of all databases currently on the server, including the database name, the owner, encoding, collation, ctype, and access privileges

SELECT datname FROM pg_database;
psql runs the query against the server and displays a list of existing databases in the output.
```

```bash
# list tables
\c [database_name]
\dt

### install pip packages

```bash
mkdir myproject
cd myproject
python3 -m venv env
source env/bin/activate
pip install -U pip
pip install django gunicorn psycopg2
```

```bash
django-admin startproject myproject ~/myproject
```

```bash
cd myproject
vim settings.py
```

```python
ALLOWED_HOSTS = ['*'] # ALLOWED_HOSTS = ['51.250.79.218']
# ^G
STATIC_ROOT = Path.joinpath(BASE_DIR, 'static')
:wq
```

```bash
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic

# 130 static files copied to '/home/yc-user/myproject/static' - that URL I gotta use in the ngenix configuration
```

### allow traffic

```bash
sudo ufw allow 8000
```
####

```bash
gunicorn --bind 0.0.0.0:8000 myproject.wsgi
```

```bash
sudo vim /etc/systemd/system/gunicorn.service
# vim
[Unit]
Description=gunicorn deamon
After=network.target

[Service]
User=yc-user
Group=www-data
WorkingDirectory=/home/yc-user/myproject
ExecStart=/home/yc-user/myproject/env/bin/gunicorn --access-logfile - --workers 3 --bind unix:/home/yc-user/myproject/myproject.sock myproject.wsgi:application

[Install]
WantedBy=multi-user.target
~
```

```bash
sudo systemctl enable gunicorn
sudo systemctl start gunicorn
sudo systemctl status gunicorn
sudo journalctl -u gunicorn
sudo systemctl daemon-reload
sudo systemctl restart gunicorn
```

### nginx

```bash
sudo vim /etc/nginx/sites-available/myproject
vim

server {
    listen 80;
    server_name 51.250.79.218;

    location = /favicon.ico { access_log off; log_not_found off; }
    location /static/ {
        root /home/yc-user/myproject/;
    }

    location / {
        include proxy_params;
        proxy_pass http://unix:/home/yc-user/myproject/myproject.sock;
    }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/myproject /etc/nginx/sites-enabled/
sudo nginx -t
```
### UFW

```bash
sudo ufw delete allow 8000
sudo ufw app list
sudo ufw allow 'Nginx Full'
sudo ufw enable
```

### log

```bash
sudo tail -F /var/log/nginx/error.log
```

### permissions

```bash
namei -nom /home/yc-user/myproject/myproject.sock
```
### postgresql

```bash
sudo systemctl start postgresql
sudo systemctl enable postgresql
sudo systemctl daemon-reload
sudo systemctl restart gunicorn
sudo nginx -t && sudo systemctl restart nginx
```

> in order to create a db you can use https://railway.app  

### settings.py

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': os.environ.get('DB_NAME'),
        'USER': os.environ.get('DB_USER'),
        'PASSWORD': os.environ.get('DB_PASSWORD'),
        'HOST': os.environ.get('DB_HOST'),
        'PORT': os.environ.get('DB_PORT'),
    }
}
```

### access to the db

```bash
psql -h localhost -U db_user -p 5432 -d db_project
```

```bash
python manage.py dbshell
```
