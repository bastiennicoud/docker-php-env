FROM composer:latest

# Create user to run composer without root and avoid permission errors with volumes sharing
RUN addgroup -g 1000 composer-www-data && adduser -G composer-www-data -g composer-www-data -s /bin/sh -D composer-www-data

WORKDIR /var/www/app
