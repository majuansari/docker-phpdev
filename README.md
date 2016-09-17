
docker-phpdev helps you to setup a php development environment using Docker

### Supported Containers
	- mysql[5.5, 5.6 & 5.7]
	- apache2
	- nginx
	- php [5.6 & 7.0]
	- phpmyadmin
	- Sonarqube


Container  | Command   | Description|
---------- | ---------- | ---------- |
php-fpm | docker-compose up -d php-fpm | PHP (cli and fpm) service|
apache2 | docker-compose up -d apache2 | Apache2|
nginx | docker-compose up -d nginx | Nginx|
mysql | docker-compose up -d mysql | mysql|
sonarqube | docker-compose up -d sonarqube | Sonarqube|
phpmyadmin | docker-compose up -d phpmyadmin | Phpmyadmin|
lamp | docker-compose up -d lamp | LAMP|
lemp | docker-compose up -d lemp | LEMP|


