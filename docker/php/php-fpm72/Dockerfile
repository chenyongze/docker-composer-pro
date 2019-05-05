FROM php:7.2.13-fpm

ADD php.ini /usr/local/etc/php/conf.d/php.ini

RUN apt-get update \
  && docker-php-ext-install pdo_mysql mysqli mbstring \
  && apt-get install -y libmemcached-dev zlib1g-dev \
  && pecl install memcached-3.1.3 swoole redis \
  && docker-php-ext-enable memcached opcache swoole redis