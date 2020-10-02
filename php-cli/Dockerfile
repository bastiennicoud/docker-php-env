FROM php:7.4-cli-alpine

RUN addgroup -g 1000 www-php-cli && adduser -G www-php-cli -g www-php-cli -s /bin/sh -D www-php-cli

RUN mkdir -p /var/www/app

RUN chown www-php-cli:www-php-cli /var/www/app

WORKDIR /var/www/app

RUN docker-php-ext-install pdo pdo_mysql

# Workaround to install pdo_pgsql, see https://github.com/docker-library/php/issues/221
RUN set -ex \
  && apk --no-cache add postgresql-dev

RUN docker-php-ext-install pdo_pgsql

# Install redis driver via pecl (need to install build dependencies before requiering phpredis)
RUN apk add --no-cache --virtual .build-deps $PHPIZE_DEPS
RUN pecl install redis-5.3.1
RUN docker-php-ext-enable redis
RUN apk del -f .build-deps
