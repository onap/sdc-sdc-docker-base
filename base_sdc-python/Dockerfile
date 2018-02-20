FROM python:2.7-alpine

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi
RUN if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi

# Install packages
RUN apk add --no-cache \
libcurl\
curl\
jq

# Install packages only needed for building
RUN apk add --no-cache --virtual .build-dependencies build-base curl-dev

# Needed for pycurl
ENV PYCURL_SSL_LIBRARY=openssl

# Pip stuff
RUN pip install influxdb pycurl requests

# Install Chef
RUN set -ex && \
    apk add --no-cache bash build-base ruby ruby-dev libffi-dev libxml2-dev && \
    gem install chef berkshelf io-console --no-document
