
docker-phpdev helps you to setup a php development environment using Docker

### Supported Containers
	- mysql[5.5, 5.6 & 5.7]
	- apache2
	- nginx
	- php [5.6 & 7.0]
	- phpmyadmin
	- Sonarqube



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
lamp | docker-compose up -d lamp |
lemp | docker-compose up -d lemp |



Commands | Description
---|---
docker-compose build               | Build the entire stack
docker-compose build {container} | Build just the specified container
docker-compose up -d | Start the entire stack
docker-compose up {container}  | Start just the specified container
docker-compose stop | Stop all the containers related to the docker-compose


