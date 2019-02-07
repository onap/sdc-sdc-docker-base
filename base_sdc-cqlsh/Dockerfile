FROM openjdk:8-jdk-alpine

RUN apk add --no-cache py-pip && \
    pip install cqlsh==4.0.1

RUN apk add --no-cache \
    bash \
    build-base \
    ruby=2.5.2-r0 \
    ruby-dev \
    libffi-dev \
    libxml2-dev
RUN gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 etc webrick --no-document --verbose --debug
