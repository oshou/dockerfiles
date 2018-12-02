FROM php:7.2-fpm-alpine
MAINTAINER oshou <adf1985adf@gmail.com>
user root

# Set Timezone
RUN apk --no-cache add tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apk del tzdata

# Set Config
COPY ./conf/www.conf /usr/local/etc/php-fpm.d/www.conf
COPY ./conf/php.ini  /usr/local/etc/php/php.ini

# Install DB-Driver
RUN echo "install mysql mysqli pdo driver" \
    && docker-php-ext-install pdo pdo_mysql mysqli \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && rm -rf /var/cache/apk/*
