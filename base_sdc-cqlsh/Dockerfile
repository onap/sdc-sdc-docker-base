FROM openjdk:8-jdk-alpine

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi
RUN if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi

RUN  apk add --no-cache \
     py-pip

RUN pip install cqlsh==4.0.1

# Install Chef
RUN set -ex && \
    apk add --no-cache bash build-base ruby ruby-dev libffi-dev libxml2-dev && \
    gem install chef berkshelf io-console --no-document