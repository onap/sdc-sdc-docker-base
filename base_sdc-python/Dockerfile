FROM python:2.7-alpine

# Install packages only needed for building
RUN  apk add --no-cache libcurl=7.59.0-r0 curl=7.59.0-r0 jq=1.5-r2 && \
     apk add --no-cache --virtual .build-dependencies build-base=0.4-r1 curl-dev=7.59.0-r0

# Needed for pycurl
ENV PYCURL_SSL_LIBRARY=openssl

# Install Chef
RUN pip install 'influxdb==5.0.0' 'pycurl== 7.43.0.1' 'requests==2.18.4' &&  \
    set -ex && \
    apk add --no-cache bash=4.3.42-r5 ruby=2.3.7-r0 ruby-dev=2.3.7-r0 libffi-dev=3.2.1-r2 libxml2-dev=2.9.5-r0 && \
    gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 --no-document && \
    echo "http://nl.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories && \
    apk update && \
    apk add binutils=2.30-r1 jq=1.6_rc1-r1 libpng=1.6.34-r1
