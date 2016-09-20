FROM ubuntu:16.04

MAINTAINER Maju Ansari

RUN locale-gen en_US.UTF-8

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt-get update \

    && apt-get install -y curl zip unzip git software-properties-common \
    && add-apt-repository -y ppa:ondrej/php \
    && apt-get update
RUN apt-cache search php5.6
RUN apt-get install -y php5.6-fpm php5.6-cli php5.6-mcrypt php5.6-gd php5.6-mysql \
       php5.6-imap php5.6-memcached php5.6-mbstring php5.6-xml \
    && apt-get remove -y --purge software-properties-common \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


#
# Configuration
#
COPY ./conf/www.conf /etc/php/5.6/fpm/pool.d/www.conf
COPY ./conf/php.ini /etc/php/5.6/mods-available/php.ini

RUN ln -s /etc/php/5.6/mods-available/php.ini /etc/php/5.6/cli/conf.d/90-php.ini && \
    ln -s /etc/php/5.6/mods-available/php.ini /etc/php/5.6/fpm/conf.d/90-php.ini && \
    mkdir -p /run/php



WORKDIR /var/www/

CMD ["php-fpm5.6"]

EXPOSE 9000

# cleanup
USER root
RUN apt-get clean && \
	rm -rfv \
	/tmp/* \
	/var/lib/apt/lists/* \
	/var/tmp/*