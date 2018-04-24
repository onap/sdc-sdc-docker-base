FROM elasticsearch:2.4.6-alpine

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi

RUN apk add --no-cache \
    curl \
    vim \
    && :

RUN mkdir -p /var/chef/nodes

# Install Chef
RUN set -ex && \
    apk add --no-cache bash build-base ruby ruby-dev libffi-dev libxml2-dev && \
    gem install chef:13.8.5 berkshelf io-console --no-document
