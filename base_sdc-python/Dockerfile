FROM nexus3.onap.org:10001/onap/integration-python:8.0.0

USER root

# Needed for pycurl
ENV PYCURL_SSL_LIBRARY=openssl

# Install packages only needed for building
RUN apk update && \
    apk add binutils jq libpng && \
    apk add --no-cache \
        libcurl \
        jq \
        bash \
        ruby=2.7.5-r0 && \
    apk add --no-cache --virtual .build-dependencies \
        libressl-dev \
        ruby-dev \
        libffi-dev \
        libxml2-dev \
        build-base \
        curl-dev && \
    # needed libcurl to install correctly
    pip install --no-cache-dir 'pycurl==7.43.0.1' &&  \
        set -ex && \
    gem install \
        chef:13.8.5 \
        berkshelf:6.3.1 \
        io-console:0.4.6 \
        etc webrick \
        --no-document && \
    apk del .build-dependencies

# user/group are the same as in integration/docker/onap-python base image
ENV user=onap group=onap

USER $user
