# commands

## install php-fpm

sudo apt install -y php-fpm

[rebrain]

user = www-data
group = www-data

listen.owner = www-data
listen.group = www-data
listen.mode = 0660

listen = /run/php/php7.4-fpm.sock

process.max = 10

### nginx

upstream php-fpm {
        server unix:/run/php/php7.4-fpm.sock;
}

server {

        listen 8081;

        server_name fhmdpe1nimn8t1raouje.51.250.2.179.nip.io;

        root /var/www/phpinfo;

        location ~ \.php {
                fastcgi_pass php-fpm;
                fastcgi_index function.phpinfo.php;
        }
}
