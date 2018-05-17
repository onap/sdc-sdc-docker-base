FROM cassandra:2.1.17

# Upgrade specific system libraries to fix CVE vulnerabilities
# avahi 0.7-3.1
#   For CVE-2017-6519
# curl 7.58.0-2
#   For CVE-2016-7167 CVE-2016-7141
# krb5 1.16-2
#   For 2018-5709 CVE-2017-15088 CVE-2017-11462
# libtiff5 4.0.9-5
#   For CVE-2018-5360
# libx11 2:1.6.5-1
#   For CVE-2016-7943 CVE-2016-7942
# libxml2 2.9.4+dfsg1-6.1
#   For CVE-2016-4448
# libxtst6 2:1.2.3-1
#   For CVE-2016-7951
# perl 5.26.2-2
#   For CVE-2017-12837 CVE-2017-12883
# python 2.7.15~rc1-1
#   For CVE-2017-1000158
# libsqlite3-0 3.23.1-1
#   For CVE-2017-10989
# libdb5.3
#   CVE-2016-3418 CVE-2016-0694 CVE-2016-0692 CVE-2016-0689 CVE-2016-0682
# libcairo2 libcairo-gobject2
#   CVE-2017-9814
# libc-bin libc6 multiarch-support
#   CVE-2018-1000001 CVE-2017-16997 CVE-2017-1000366 CVE-2015-5180 CVE-2016-5417 CVE-2018-6485 CVE-2017-15804 CVE-2017-15670 CVE-2014-9984 CVE-2014-9761 CVE-2015-8983 CVE-2015-8982
# libgtk2.0-0 libgtk2.0-common
#   CVE-2014-1949
# libharfbuzz0b
#   CVE-2015-8947 CVE-2016-2052
# libgcrypt20
#   CVE-2017-0379
# libtasn1-6
#   CVE-2018-6003 CVE-2017-10790
# libxi6
#   CVE-2016-7946 CVE-2016-7945
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
      apt-utils=1.0.9.8.4 \
      openjdk-8-jdk \
      libavahi-client3=0.7-4 libavahi-common-data=0.7-4 libavahi-common3=0.7-4 \
      curl=7.58.0-2 libcurl3=7.58.0-2 \
      krb5-locales=1.16-2 libgssapi-krb5-2=1.16-2 libkrb5-3=1.16-2 libkrb5support0=1.16-2 \
      libtiff5=4.0.9-5 \
      libx11-6=2:1.6.5-1 libx11-data=2:1.6.5-1 libx11-xcb1=2:1.6.5-1 \
      libxml2=2.9.4+dfsg1-6.1 \
      libxtst6=2:1.2.3-1 \
      perl=5.26.2-3 \
      python=2.7.15~rc1-1 \
      libsqlite3-0=3.23.1-1 \
      libdb5.3=5.3.28-13.1+b1 \
      libcairo2=1.15.10-3 libcairo-gobject2=1.15.10-3 \
      libc-bin=2.27-3 libc6=2.27-3 multiarch-support=2.27-3 \
      libgtk2.0-0=2.24.32-1 libgtk2.0-common=2.24.32-1 \
      libharfbuzz0b=1.7.6-1 \
      libgcrypt20=1.8.2-2 \
      libtasn1-6=4.13-2 \
      libxi6=2:1.7.9-1 \
      libldap-2.4-2=2.4.44+dfsg-5+deb9u1 \
      libpcre3=2:8.39-9 \
      passwd=1:4.5-1 \
      zlib1g=1:1.2.11.dfsg-1 \
      ntp=1:4.2.8p11+dfsg-1 && \
    apt-get -y autoremove


RUN update-alternatives --set java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java

RUN curl -L https://omnitruck.chef.io/install.sh | bash

