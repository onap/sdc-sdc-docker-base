FROM ubuntu:16.04

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi
RUN if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi 

RUN apt-get -y update && apt-get -y install --no-install-recommends \
    apt-utils \
    curl \
    default-jre \
    openjdk-8-jdk \
    vim

# Set Java links
RUN update-alternatives --set java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java

# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

