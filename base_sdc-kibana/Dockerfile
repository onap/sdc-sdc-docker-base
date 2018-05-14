FROM kibana:4.3.3

# Upgrade specific system libraries to fix CVE vulnerabilities
# bash 4.4.18-2+b1
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
# wget 1.19.5-1
#   For CVE-2017-13090 CVE-2017-13089 CVE-2016-7098
# libdb5.3
#   CVE-2016-3418 CVE-2016-0694 CVE-2016-0692 CVE-2016-0689 CVE-2016-0682
# libc-bin libc6 multiarch-support
#   CVE-2018-1000001 CVE-2017-16997 CVE-2017-1000366 CVE-2015-5180 CVE-2016-5417 CVE-2018-6485 CVE-2017-15804 CVE-2017-15670 CVE-2014-9984 CVE-2014-9761 CVE-2015-8983 CVE-2015-8982
# libgnutls30
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

RUN echo "deb http://deb.debian.org/debian stretch main" >> /etc/apt/sources.list && \
    echo "deb http://deb.debian.org/debian stretch-updates main" >> /etc/apt/sources.list && \
    echo "deb http://security.debian.org stretch/updates main" >> /etc/apt/sources.list && \
    echo "deb http://deb.debian.org/debian buster main" >> /etc/apt/sources.list && \
    echo "deb http://deb.debian.org/debian buster-updates main" >> /etc/apt/sources.list && \
    echo "deb http://security.debian.org buster/updates main" >> /etc/apt/sources.list && \
    apt-get -y update && \
    apt-get -y --no-install-recommends install \
      vim=2:7.4.488-7+deb8u3 vim-common=2:7.4.488-7+deb8u3 vim-runtime=2:7.4.488-7+deb8u3 \
      bash=4.4.18-2+b1 \
      curl=7.58.0-2 libcurl3=7.58.0-2 \
      krb5-locales=1.16-2 libgssapi-krb5-2=1.16-2 libkrb5-3=1.16-2 libkrb5support0=1.16-2 \
      openssl=1.1.0h-2 \
      perl-base=5.26.2-3 \
      systemd=238-4 \
      wget=1.19.5-1 \
      libdb5.3=5.3.28-13.1+b1 \
      libc-bin=2.27-3 libc6=2.27-3 multiarch-support=2.27-3 \
      libgnutls30=3.5.18-1 \
      libgcrypt20=1.8.2-2 \
      libtasn1-6=4.13-2 \
      libldap-2.4-2=2.4.44+dfsg-5+deb9u1 \
      libpcre3=2:8.39-9 \
      passwd=1:4.5-1 \
      zlib1g=1:1.2.8.dfsg-5 && \
    apt-get -y autoremove

# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

