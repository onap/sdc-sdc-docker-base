FROM cassandra:2.1.17

RUN apt-get -y update && \
    apt-get -y install --no-install-recommends \
    curl=7.38.0-4+deb8u10 \
    vim=2:7.4.488-7+deb8u3 \
    apt-utils=1.0.9.8.4 \
    openjdk-8-jdk=8u162-b12-1~bpo8+1 \
    python=2.7.9-1

RUN update-alternatives --set java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java

RUN curl -L https://omnitruck.chef.io/install.sh | bash

