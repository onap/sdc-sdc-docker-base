FROM kibana:4.3.3

ARG HTTP_PROXY
ARG HTTPS_PROXY

ENV HTTP_PROXY  ${HTTP_PROXY}
ENV HTTPS_PROXY ${HTTPS_PROXY}

RUN if [ ! -z ${HTTP_PROXY} ]; then echo "Acquire::http::proxy  \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf; fi && \
    if [ ! -z ${HTTPS_PROXY} ]; then echo "Acquire::https::proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf; fi 

RUN apt-get -y update && apt-get -y install \
    curl \
    vim

# Upgrade specific system libraries to fix CVE vulnerabilities
# bash 4.4.18-2
#   For CVE-2016-0634 CVE-2016-7543
# curl 7.58.0-2
#   For CVE-2016-7167 CVE-2016-7141
# krb5 1.16-2
#   For CVE-2018-5709 CVE-2017-15088 CVE-2017-11462
# openssl 1.1.0h-2
#   For CVE-2016-8610 CVE-2017-3731 CVE-2016-6302 CVE-2016-2181 CVE-2016-2179 CVE-2016-2180 CVE-2016-2109 CVE-2016-2106 CVE-2016-2105 CVE-2016-6303 CVE-2016-2182 CVE-2016-2177 CVE-2016-2176
# perl 5.26.2-2
#   For CVE-2017-12837 CVE-2017-12883
# systemd 238-4
#   For CVE-2017-1000082 CVE-2017-9445 CVE-2017-9217
# wget 1.19.4-1
#   For CVE-2017-13090 CVE-2017-13089 CVE-2016-7098
# libdb5.3
#   CVE-2016-3418 CVE-2016-0694 CVE-2016-0692 CVE-2016-0689 CVE-2016-0682
# libc-bin libc6 multiarch-support
#   CVE-2018-1000001 CVE-2017-16997 CVE-2017-1000366 CVE-2015-5180 CVE-2016-5417 CVE-2018-6485 CVE-2017-15804 CVE-2017-15670 CVE-2014-9984 CVE-2014-9761 CVE-2015-8983 CVE-2015-8982
# libgnutls-deb0-28
#   CVE-2017-5335 CVE-2017-5337 CVE-2017-5334
# libgcrypt20
#   CVE-2017-0379
# libtasn1-6
#   CVE-2018-6003 CVE-2017-10790
# libldap-2.4-2
#   CVE-2017-17740
# libpcre3
#   CVE-2015-3217
# passwd
#   CVE-2017-12424
# zlib1g
#   CVE-2016-9843 CVE-2016-9841 CVE-2016-9842 CVE-2016-9840

RUN echo "deb http://deb.debian.org/debian buster main" >> /etc/apt/sources.list && \
    echo "deb http://deb.debian.org/debian buster-updates main" >> /etc/apt/sources.list && \
    echo "deb http://security.debian.org buster/updates main" >> /etc/apt/sources.list && \
    apt-get -y update && \
    apt-get -y --only-upgrade install \
      bash \
      libcurl3 curl \
      krb5-locales libgssapi-krb5-2 libkrb5-3 libkrb5support0 \
      openssl \
      perl-base \
      systemd \
      wget \
      libdb5.3 \
      libc-bin libc6 multiarch-support \
      libgnutls-deb0-28 \
      libgcrypt20 \
      libtasn1-6 \
      libldap-2.4-2 \
      libpcre3 \
      passwd \
      zlib1g && \
    apt-get -y autoremove

# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

