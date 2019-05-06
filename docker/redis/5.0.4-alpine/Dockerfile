FROM redis:5.0.4-alpine
MAINTAINER Yongze Chen <yongze@dingtalk.com>

COPY ./conf/redis.conf /usr/local/etc/redis.conf
COPY ./data /usr/local/redis/data
CMD [ "redis-server", "/usr/local/etc/redis.conf" ]