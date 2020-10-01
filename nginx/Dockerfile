FROM nginx:stable-alpine

ADD ./nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /var/www/app

RUN addgroup -g 1000 nginx-www-data && adduser -G nginx-www-data -g nginx-www-data -s /bin/sh -D nginx-www-data

RUN chown nginx-www-data:nginx-www-data /var/www/app
