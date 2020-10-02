FROM php:7.4-fpm-alpine

ADD ./www.conf /usr/local/etc/php-fpm.d/www.conf

RUN addgroup -g 1000 www-php-fpm && adduser -G www-php-fpm -g www-php-fpm -s /bin/sh -D www-php-fpm

RUN mkdir -p /var/www/app

RUN chown www-php-fpm:www-php-fpm /var/www/app

WORKDIR /var/www/app

RUN docker-php-ext-install pdo pdo_mysql opcache

# Workaround to install pdo_pgsql, see https://github.com/docker-library/php/issues/221
RUN set -ex \
  && apk --no-cache add postgresql-dev

RUN docker-php-ext-install pdo_pgsql

# Install redis driver via pecl (need to install build dependencies before requiering phpredis)
RUN apk add --no-cache --virtual .build-deps $PHPIZE_DEPS
RUN pecl install redis-5.3.1
RUN docker-php-ext-enable redis
RUN apk del -f .build-deps

ADD ./opcache.ini $PHP_INI_DIR/conf.d/opcache.ini
