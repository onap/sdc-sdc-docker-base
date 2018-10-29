FROM openjdk:8-jdk-alpine

# Install Chef
RUN set -ex && \
    apk add --no-cache \
    curl \
    vim \
    bash \
    build-base \
    ruby=2.5.2-r0 \
    ruby-dev \
    libffi-dev \
    libxml2-dev && \
    gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 etc webrick --no-document && \
    echo "http://nl.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories && \
    apk update && \
    apk add binutils curl libcurl libtasn1
