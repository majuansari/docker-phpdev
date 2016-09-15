FROM ubuntu:16.04

MAINTAINER Maju Ansari

RUN apt-get update
RUN apt-get -y install nginx
# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

ADD ./conf/nginx.conf /etc/nginx/

RUN rm /etc/nginx/sites-available/default
COPY sites/*.conf /etc/nginx/sites-available/

ARG PHP_UPSTREAM=php-fpm:9000

RUN echo "upstream php-upstream { server ${PHP_UPSTREAM}; }" > /etc/nginx/conf.d/upstream.conf

RUN apt-get clean \
        && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \

CMD ["nginx"]

EXPOSE 81 443
