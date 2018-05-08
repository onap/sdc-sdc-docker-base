FROM openjdk:8-jdk-alpine

# Install Chef
RUN set -ex && \
    apk add --no-cache curl vim bash=4.4.19-r1 build-base=0.5-r0 ruby=2.4.4-r0 ruby-dev=2.4.4-r0 libffi-dev=3.2.1-r4 libxml2-dev=2.9.7-r0 && \
    gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 --no-document && \
    echo "http://nl.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories && \
    apk update && \
    apk add binutils=2.30-r1 curl=7.59.0-r1 libcurl=7.59.0-r1 libtasn1=4.13-r0
