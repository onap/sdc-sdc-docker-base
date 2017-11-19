FROM jetty:9.3-jre8-alpine

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi

USER root

RUN apk add --no-cache \
    jq \
    curl \
    curl-dev \
    openssl-dev \
    python \
    python-dev \
    py-pip \
    py-setuptools \
    vim \
    && :

# Install Chef
RUN set -ex && \
    apk add --no-cache bash build-base ruby ruby-dev libffi-dev libxml2-dev && \
    gem install chef berkshelf io-console --no-document

RUN pip install pycurl

USER jetty

