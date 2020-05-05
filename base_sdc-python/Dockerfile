FROM python:2.7-alpine

# Needed for pycurl
ENV PYCURL_SSL_LIBRARY=openssl

# Install packages only needed for building
RUN apk update && \
    apk add binutils jq libpng && \
    apk add --no-cache \
        libcurl \
        curl \
        jq \
        libressl-dev \
        bash \
        ruby=2.6.6-r2 \
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

RUN addgroup -g 1000 sdc && adduser -S -u 1000 -G sdc -s /bin/sh sdc

USER sdc
