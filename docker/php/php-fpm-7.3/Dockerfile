FROM daocloud.io/library/php:7.3.2-fpm-alpine3.8
MAINTAINER Yongze Chen <yongze@dingtalk.com>

# Set Timezone Environments
ENV TIMEZONE  Asia/Shanghai
RUN apk add --update tzdata  \
    && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime  \
    && echo "${TIMEZONE}" > /etc/timezone  \
    && apk add autoconf \
    && apk del tzdata  \
    && docker-php-ext-configure mysqli  \
    && docker-php-ext-install mysqli \
    && ln -sf /dev/stdout /usr/local/var/log/php-fpm.access.log  \
    && ln -sf /dev/stderr /usr/local/var/log/php-fpm.error.log