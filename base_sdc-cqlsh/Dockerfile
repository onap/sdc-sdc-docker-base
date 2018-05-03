FROM openjdk:8-jdk-alpine

RUN apk add --no-cache py-pip && \
    pip install cqlsh==4.0.1 && \
    set -ex && \
    apk add --no-cache bash=4.4.19-r1 build-base=0.5-r0 ruby=2.4.4-r0 ruby-dev=2.4.4-r0 libffi-dev=3.2.1-r4 libxml2-dev=2.9.7-r0 && \
    gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 --no-document
