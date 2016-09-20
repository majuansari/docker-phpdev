FROM ubuntu:16.04

MAINTAINER Maju Ansari

#
# Set environment variables
#
ENV DEBIAN_FRONTEND=noninteractive

#
# User
#
RUN groupmod -g 1000 www-data && \
    usermod -u 1000 www-data

#
# APT packages
#
RUN apt-get update && apt-get install -y \
    apache2 \
    vim


RUN rm -rf /var/lib/apt/lists/*

#
# Configuration
#
RUN rm /etc/apache2/sites-enabled/* && \
    rm /etc/apache2/sites-available/*


RUN a2dismod mpm_event && \
    a2enmod deflate headers macro mpm_worker proxy proxy_fcgi rewrite ssl vhost_alias



ARG WEB_DOCUMENT_ROOT="/var/www/"

ARG PHP_SOCKET="php-fpm:9000"

#
# Enabling vhosts
#
ADD ./config/* /etc/apache2/sites-available/
WORKDIR /etc/apache2/sites-available
RUN a2ensite *

#
# Reset environment variables
#
ENV DEBIAN_FRONTEND=

RUN echo "export APACHE_WEB_PHP_SOCKET='$PHP_SOCKET'" >> "/etc/apache2/envvars"
RUN echo "export APACHE_WEB_DOCUMENT_ROOT='$WEB_DOCUMENT_ROOT'" >> "/etc/apache2/envvars"

#
# Command
#
WORKDIR /var/www/
COPY ./apache2-foreground /usr/local/bin/
CMD ["apache2-foreground"]

# cleanup
USER root
RUN apt-get clean && \
	rm -rfv \
	/tmp/* \
	/var/lib/apt/lists/* \
	/var/tmp/*

