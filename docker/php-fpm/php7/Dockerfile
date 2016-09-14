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
    && apt-get remove -y --purge software-properties-common \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#
#--------------------------------------------------------------------------
# Final Touch
#--------------------------------------------------------------------------
#



ADD ./conf/phpdev.ini /usr/local/etc/php5.6/conf.d
ADD ./conf/phpdev.pool.conf /usr/local/etc/ph5.6-fpm.d/
#COPY ./app/ /var/www
RUN usermod -u 1000 www-data

WORKDIR /var/www/


CMD ["/bash"]

EXPOSE 9000