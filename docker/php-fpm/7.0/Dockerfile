FROM ubuntu:16.04

MAINTAINER Maju Ansari

RUN locale-gen en_US.UTF-8

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt-get update \

    && apt-get install -y curl zip unzip git software-properties-common \
    && add-apt-repository -y ppa:ondrej/php \
    && apt-get update \
    && apt-get install -y php7.0-fpm php7.0-cli php7.0-mcrypt php7.0-gd php7.0-mysql \
       php7.0-pgsql php7.0-imap php-memcached php7.0-mbstring php7.0-xml \
    && apt-get remove -y --purge software-properties-common

#
# Configuration
#
COPY ./conf/www.conf /etc/php/7.0/fpm/pool.d/www.conf
COPY ./conf/php.ini /etc/php/7.0/mods-available/php.ini

RUN ln -s /etc/php/7.0/mods-available/php.ini /etc/php/7.0/cli/conf.d/90-php.ini && \
    ln -s /etc/php/7.0/mods-available/php.ini /etc/php/7.0/fpm/conf.d/90-php.ini && \
    mkdir -p /run/php

# Configure FPM to run properly on docker
RUN  usermod -u 1000 www-data

WORKDIR /var/www/

CMD ["php-fpm7.0"]

EXPOSE 9000
# cleanup
USER root
RUN apt-get clean && \
	rm -rfv \
	/tmp/* \
	/var/lib/apt/lists/* \
	/var/tmp/*