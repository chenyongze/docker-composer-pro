FROM php:7.3.5-fpm-alpine3.9
MAINTAINER Yongze Chen <yongze@dingtalk.com>

# Set Timezone Environments
ENV TIMEZONE  Asia/Shanghai
ENV SWOOLE_VERSION 4.3.3
ENV REDIS_VERSION 4.3.0
#RUN apk add --no-cache --virtual .build-deps \
#处理墙问题
RUN echo "处理墙问题....."
RUN echo "192.30.253.112	github.com" >> /etc/hosts
RUN echo "151.101.72.133	assets-cdn.github.com" >> /etc/hosts
RUN echo "151.101.193.194	github.global.ssl.fastly.net" >> /etc/hosts
#资源替换 国内阿里
ADD ./alpine-conf/repositories /etc/apk/repositories

RUN apk add --no-cache --virtual .build-deps \
             tzdata \
             curl \
             g++ \
             make \
             autoconf \
             openssl-dev  \
             libaio  \
             libaio-dev \
             linux-headers \
             zlib-dev \
             libzip-dev \
             bash \
             openssh \
             libxslt-dev \
             libjpeg-turbo-dev \
             libwebp-dev \
             libpng-dev \
             libxml2-dev \
             freetype-dev \
             libmcrypt \
             freetds-dev  \
             libmemcached-dev  \
             cyrus-sasl-dev  \
    && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime  \
    && echo "${TIMEZONE}" > /etc/timezone  \
    && docker-php-source extract  \
    && docker-php-ext-configure pdo  \
    && docker-php-ext-configure pdo_mysql  \
    && docker-php-ext-configure mysqli  \
    && docker-php-ext-configure opcache  \
    && docker-php-ext-configure exif  \
    && docker-php-ext-configure sockets  \
    && docker-php-ext-configure soap  \
    && docker-php-ext-configure bcmath  \
    && docker-php-ext-configure pcntl  \
    && docker-php-ext-configure sysvsem  \
    && docker-php-ext-configure tokenizer  \
    && docker-php-ext-configure shmop  \
    && docker-php-ext-configure gd \
        --with-jpeg-dir=/usr/include \
        --with-png-dir=/usr/include \
        --with-webp-dir=/usr/include \
        --with-freetype-dir=/usr/include  \
    && docker-php-ext-install pdo \
       pdo_mysql \
       mysqli \
       opcache \
       exif \
       sockets \
       soap \
       bcmath \
       pcntl \
       sysvsem \
       tokenizer \
       shmop \
    && docker-php-source delete \
    && apk del .build-deps  \
    && ln -sf /dev/stdout /usr/local/var/log/php-fpm.access.log  \
    && ln -sf /dev/stderr /usr/local/var/log/php-fpm.error.log  \
    && cd ~ \
#    && wget https://github.com/swoole/swoole-src/archive/v"${SWOOLE_VERSION}".tar.gz \
#    && tar -zxvf v"${SWOOLE_VERSION}".tar.gz    \
#    && mkdir -p /usr/src/php/ext \
#    && mv swoole-src-"${SWOOLE_VERSION}" /usr/src/php/ext/swoole \
#    && docker-php-ext-install swoole \
#    composer 处理
#    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer   \
#    && curl --location --output /usr/local/bin/phpunit https://phar.phpunit.de/phpunit.phar  \
#    && chmod +x /usr/local/bin/phpunit  \
    && wget https://github.com/phpredis/phpredis/archive/"${REDIS_VERSION}".tar.gz \
    && tar -zxvf "${REDIS_VERSION}".tar.gz \
    && mkdir -p /usr/src/php/ext \
    && mv phpredis-"${REDIS_VERSION}" /usr/src/php/ext/redis \
    && rm -rf "${REDIS_VERSION}".tar.gz \
    && docker-php-ext-install redis