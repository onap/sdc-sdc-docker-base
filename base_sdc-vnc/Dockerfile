FROM consol/ubuntu-xfce-vnc:1.3.0

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

USER 0

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi

RUN apt-get -y update && apt-get -y install curl

# install chef-solo
RUN curl -L  https://www.opscode.com/chef/install.sh | bash

# install java
RUN apt-get -y update && apt-get -y install default-jre
