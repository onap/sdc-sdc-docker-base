FROM kibana:4.3.3

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi 

# Install specific system libraries to fix CVE vulnerabilities
# bash 4.4-5
#   For CVE-2016-7543
# curl 7.52.1-5+deb9u4
#   For CVE-2016-7167
# krb5 1.16-2
#   For CVE-2017-15088 CVE-2017-11462
# openssl 1.1.0h-2
#   For CVE-2016-6303 CVE-2016-2182 CVE-2016-2177 CVE-2016-2176
# perl 5.26.1-6
#   For CVE-2017-12883
# systemd 234-4
#   For CVE-2017-1000082
# wget 1.19.4-1
#   For CVE-2017-13090 CVE-2017-13089 CVE-2016-7098

RUN echo "deb http://ftp.de.debian.org/debian stretch main" >> /etc/apt/sources.list && \
    echo "deb http://ftp.de.debian.org/debian buster main" >> /etc/apt/sources.list && \
    apt-get -y update && \
    apt-get -y install \
    vim \
    bash=4.4-5 \
    libcurl3=7.52.1-5+deb9u4 curl=7.52.1-5+deb9u4 \
    krb5-locales=1.16-2 libgssapi-krb5-2=1.16-2 libkrb5-3=1.16-2 libkrb5support0=1.16-2 \
    openssl=1.1.0h-2 \
    perl-base=5.26.1-6 \
    systemd=238-4 \
    wget=1.19.4-1


# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

