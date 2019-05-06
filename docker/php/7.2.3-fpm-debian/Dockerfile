FROM php:7.2.13-fpm
MAINTAINER Yongze Chen <yongze@dingtalk.com>

ADD php.ini /usr/local/etc/php/conf.d/php.ini
RUN apt-get update \
  && docker-php-ext-install pdo_mysql mysqli mbstring \
  && apt-get install -y libmemcached-dev    \
#  && pecl install memcached-3.1.3 swoole redis \
  && pecl install swoole redis \
  && docker-php-ext-enable opcache swoole redis