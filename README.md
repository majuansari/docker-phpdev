
docker-phpdev helps you to setup a php development environment using Docker

### Containers
	- mysql[5.5, 5.6 & 5.7]
	- apache2
	- nginx
	- php [5.6 & 7.0]
	- phpmyadmin
	- sonarqube
	- redis
	- memcached
	- mailcatcher


###  Features

> - Easy setup of lemp & lamp environments
> - Easy vhost setup
> - Try out multiple versions of php & mysql
> - Usefull softwares and extensions added
> - Low size containers
> - Only ubuntu 16.04 or alpine as base images

 
###### # Setup LAMP environment
```
git clone https://github.com/majuansari/docker-phpdev.git
cd docker-phpdev

//Start lamp environment using short key
docker-compose up -d lamp

//Start lamp environment by specifying services
docker-compose up -d mysql apache2 php-fpm

```


###### # Setup LEMP environment
```
git clone https://github.com/majuansari/docker-phpdev.git
cd docker-phpdev
//Start lamp environment using short key
docker-compose up -d lemp

//Start lamp environment by specifying services
docker-compose up -d mysql nginx php-fpm
```

###### # Add vhosts

> For adding vhosts create conf files in *docker/apache2/conf* for apache2 and *docker/nginx/sites* for nginx

### Editing docker-compose.yml

###### # Change php versions


```
\\php 5.6 setting
     php-fpm:
        build:
            context: ./docker/php-fpm/php56
        volumes_from:
            - volumes_source
        expose:
            - "9000"
        links:
            - codebox

\\For changing to php 7.0 setting change the context value as below
    php-fpm:
        build:
            context: ./docker/php-fpm/php7
        volumes_from:
            - volumes_source
        expose:
            - "9000"
        links:
            - codebox

```
###### # Change mysql versions
```
\\mysql 5.6 configuration
    mysql:
        build:
            context: ./docker/mysql/5.6
        volumes_from:
            - volumes_data
        ports:
            - "3306:3306"
        environment:
            MYSQL_DATABASE: test
            MYSQL_USER: maju
            MYSQL_PASSWORD: 1234maju
            MYSQL_ROOT_PASSWORD: 1234maju


\\For changing to mysql5.7  change the context value as below
    mysql:
        build:
            context: ./docker/mysql/5.7
        volumes_from:
            - volumes_data
        ports:
            - "3306:3306"
        environment:
            MYSQL_DATABASE: test
            MYSQL_USER: maju
            MYSQL_PASSWORD: 1234maju
            MYSQL_ROOT_PASSWORD: 1234maju

\\For changing to mysql5.5  change the context value as below
    mysql:
        build:
            context: ./docker/mysql/5.5
        volumes_from:
            - volumes_data
        ports:
            - "3306:3306"
        environment:
            MYSQL_DATABASE: test
            MYSQL_USER: maju
            MYSQL_PASSWORD: 1234maju
            MYSQL_ROOT_PASSWORD: 1234maju

```

Container  | Command   |
---------- | ---------- |
php-fpm | docker-compose up -d php-fpm |
apache2 | docker-compose up -d apache2 |
nginx | docker-compose up -d nginx |
mysql | docker-compose up -d mysql |
sonarqube | docker-compose up -d sonarqube |
phpmyadmin | docker-compose up -d phpmyadmin |
redi | docker-compose up -d redis |
mailcatcher | docker-compose up -d mailcatcher |
memcached | docker-compose up -d memcached |
lamp | docker-compose up -d lamp |
lemp | docker-compose up -d lemp |



Commands | Description
---|---
docker-compose build               | Build the entire stack
docker-compose build {container} | Build just the specified container
docker-compose up -d | Start the entire stack
docker-compose up {container}  | Start just the specified container
docker-compose stop | Stop all the containers related to the docker-compose

![alt tag](https://raw.githubusercontent.com/majuansari/docker-phpdev/master/docker-useful-commands.png)

### References

1. [Docker for php developers](http://www.newmediacampaigns.com/blog/docker-for-php-developers)
2. [PHP Web development with docker](http://mmenozzi.github.io/2016/01/22/php-web-development-with-docker/)
3. [webdevops docker](https://github.com/webdevops/Dockerfile)
4. [laradock](https://github.com/LaraDock/laradock)
5. [ php-dockerized](https://github.com/kasperisager/php-dockerized)
