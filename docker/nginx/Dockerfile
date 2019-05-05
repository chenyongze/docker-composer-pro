FROM nginx
MAINTAINER Yongze Chen <yongze@dingtalk.com>

ADD ./conf/nginx.conf /etc/nginx/nginx.conf
ADD ./conf/fastcgi.conf /etc/nginx/fastcgi.conf
ADD ./conf/server.conf /etc/nginx/conf.d/default.conf
#ADD localhost.key /etc/ssl/private/localhost.key
#ADD localhost.crt /etc/ssl/certs/localhost.crt