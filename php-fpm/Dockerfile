FROM php:7.4-fpm-alpine

ADD ./www.conf /usr/local/etc/php-fpm.d/www.conf

RUN addgroup -g 1000 www-php-fpm && adduser -G www-php-fpm -g www-php-fpm -s /bin/sh -D www-php-fpm

RUN mkdir -p /var/www/app

RUN chown www-php-fpm:www-php-fpm /var/www/app

WORKDIR /var/www/app

RUN docker-php-ext-install pdo pdo_mysql
