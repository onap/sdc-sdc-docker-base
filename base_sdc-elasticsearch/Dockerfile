FROM elasticsearch:2.1.2

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi

RUN apt-get -y update && apt-get -y install \
    apt-utils \
    curl \
    vim

RUN mkdir -p /var/chef/nodes

# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

