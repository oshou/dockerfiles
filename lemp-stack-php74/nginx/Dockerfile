FROM nginx:1.15-alpine

WORKDIR /var/www/html

COPY ./conf/nginx.conf   /etc/nginx/nginx.conf

RUN set -x \
    && apk --no-cache add tzdata \
    && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && apk del tzdata

EXPOSE 80 443
