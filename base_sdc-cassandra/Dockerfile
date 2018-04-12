FROM cassandra:2.1.17

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi 

#ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -y update && apt-get -y install --no-install-recommends \
    curl   \
    vim \
    apt-utils  \
    openjdk-8-jdk \
    python

RUN update-alternatives --set java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java


# Install specific system libraries to fix CVE vulnerabilities
# avahi 0.7-3.1
#   For CVE-2017-6519
# curl 7.52.1-5+deb9u4
#   For CVE-2016-7167
# krb5 1.16-2
#   For CVE-2017-15088 CVE-2017-11462
# libtiff5 4.0.8-2+deb9u2
#   For CVE-2018-5360
# libx11 2:1.6.4-3
#   For CVE-2016-7943 CVE-2016-7942
# libxml2 2.9.4+dfsg1-6.1
#   For CVE-2016-4448
# libxtst6 2:1.2.3-1
#   For CVE-2016-7951
# perl 5.26.1-5
#   For CVE-2017-12883
# python 2.7.14-4
#   For CVE-2017-1000158
# libsqlite3-0 3.23.0-1
#   For CVE-2017-10989

RUN echo "deb http://ftp.de.debian.org/debian stretch main" >> /etc/apt/sources.list && \
    echo "deb http://ftp.de.debian.org/debian buster main" >> /etc/apt/sources.list && \
    apt-get -y update && \
    apt-get -y install \
    libavahi-client3=0.7-3.1 libavahi-common-data=0.7-3.1 libavahi-common3=0.7-3.1 \
    libcurl3=7.52.1-5+deb9u4 curl=7.52.1-5+deb9u4 \
    krb5-locales=1.16-2 libgssapi-krb5-2=1.16-2 libkrb5-3=1.16-2 libkrb5support0=1.16-2 \
    libtiff5=4.0.8-2+deb9u2 \
    libx11-6=2:1.6.4-3 libx11-data=2:1.6.4-3 libx11-xcb1=2:1.6.4-3 \
    libxml2=2.9.4+dfsg1-6.1 \
    libxtst6=2:1.2.3-1 \
    perl-base=5.26.1-5 \
    python=2.7.14-4 \
    libsqlite3-0=3.23.0-1


# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

