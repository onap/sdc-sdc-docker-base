FROM cassandra:3.11.4
RUN mv /etc/apt/sources.list.d/cassandra.list /tmp && \
    apt-get -o Acquire::Check-Valid-Until=false update && \
    mv /tmp/cassandra.list /etc/apt/sources.list.d/cassandra.list
RUN apt-get -y --no-install-recommends install \
      apt-transport-https \
      curl \
      wget && \
    apt-get -y --no-install-recommends install \
      perl \
      python \
      ntp && \
    apt-get -y autoremove && \
    update-alternatives --set java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java && \
    curl -L https://omnitruck.chef.io/install.sh | bash -s -- -v 13.8.5

