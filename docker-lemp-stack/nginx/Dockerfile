FROM nginx:1.15-alpine
MAINTAINER oshou <adf1985adf@gmail.com>
user root

# Set Timezone
RUN apk --no-cache add tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apk del tzdata

# Set Config
COPY ./conf/nginx.conf   /etc/nginx/nginx.conf
COPY ./conf/default.conf /etc/nginx/conf.d/default.conf
