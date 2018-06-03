FROM python:2.7-alpine

# Install packages only needed for building
RUN  apk add --no-cache libcurl=7.60.0-r1 curl=7.60.0-r1 jq=1.5-r5 libressl-dev=2.6.4-r2 && \
     apk add --no-cache --virtual .build-dependencies build-base=0.5-r0 curl-dev=7.60.0-r1

# Needed for pycurl
ENV PYCURL_SSL_LIBRARY=openssl

# Install Chef
RUN pip install 'influxdb==5.0.0' 'pycurl==7.43.0.1' 'requests==2.18.4' &&  \
    set -ex && \
    apk add --no-cache bash=4.4.19-r1 ruby=2.4.4-r0 ruby-dev=2.4.4-r0 libffi-dev=3.2.1-r4 libxml2-dev=2.9.7-r0 && \
    gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 --no-document && \
    echo "http://nl.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories && \
    apk update && \
    apk add binutils=2.30-r1 jq=1.6_rc1-r1 libpng=1.6.34-r1
