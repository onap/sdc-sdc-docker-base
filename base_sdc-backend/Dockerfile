FROM jetty:9.3-jre8

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi


USER root

RUN apt-get -y update && apt-get -y install \
    apt-utils \
    curl \
    vim \
    jq \
    python \
    libssl-dev \
    libcurl4-openssl-dev \
    python-dev \
    gcc \
    python-pip

# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

RUN pip install pycurl

USER jetty

