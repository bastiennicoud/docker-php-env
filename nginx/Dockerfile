FROM nginx:stable-alpine

ADD ./nginx.conf /etc/nginx/nginx.conf
# ADD ./nginx/default.conf /etc/nginx/conf.d/default.conf

RUN mkdir -p /var/www/app

RUN addgroup -g 1000 www-data && adduser -G www-data -g www-data -s /bin/sh -D www-data

RUN chown www-data:www-data /var/www/app

RUN rm /etc/nginx/conf.d/default.conf
