FROM elasticsearch:2.4.6-alpine

RUN mkdir -p /var/chef/nodes

# Install Chef
RUN set -ex && \
    apk add --no-cache \
        linux-headers \
        curl \
        vim \
        bash \
        build-base \
        ruby=2.5.5-r0 \
        ruby-dev \
        libffi-dev \
        libxml2-dev && \
    gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 etc webrick --no-document && \
    echo "http://nl.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories && \
    apk update && \
    apk add binutils curl libcurl libtasn1
