FROM golang:1.12.4-alpine3.9

#资源替换 国内阿里
ADD ./alpine-conf/repositories /etc/apk/repositories

RUN apk add --no-cache --virtual .build-deps \
             curl \
             g++ \
             make \
             autoconf \
             git
#     && apk del .build-deps

#安装dep
#go get -u github.com/golang/dep/cmd/dep
#安装 govendor
#go get -u github.com/kardianos/govendor
