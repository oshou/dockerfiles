FROM php:7.4-fpm-alpine

WORKDIR /var/www/html

# Set Config
COPY ./conf/www.conf /usr/local/etc/php-fpm.d/www.conf
COPY ./conf/php.ini  /usr/local/etc/php/php.ini

RUN set -x \
    && apk --no-cache add tzdata \
    && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && apk del tzdata \
    && docker-php-ext-install pdo pdo_mysql mysqli \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && rm -rf /var/cache/apk/*

EXPOSE 9000
