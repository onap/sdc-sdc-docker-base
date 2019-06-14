FROM python:2.7-alpine

# Needed for pycurl
ENV PYCURL_SSL_LIBRARY=openssl

# Install packages only needed for building
RUN echo "http://nl.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories && \
    apk update && \
    apk add binutils jq libpng && \
    apk add --no-cache \
        libcurl \
        curl \
        jq \
        libressl-dev \
        bash \
        ruby=2.5.5-r0 \
        ruby-dev \
        libffi-dev \
        libxml2-dev && \
    apk add --no-cache --virtual .build-dependencies \
        build-base \
        curl-dev && \
    pip install 'influxdb==5.0.0' 'pycurl==7.43.0.1' 'requests==2.18.4' &&  \
        set -ex && \
    gem install \
        chef:13.8.5 \
        berkshelf:6.3.1 \
        io-console:0.4.6 \
        etc webrick \
        --no-document





