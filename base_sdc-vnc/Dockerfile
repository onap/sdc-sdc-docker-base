FROM consol/ubuntu-xfce-vnc:1.3.0

USER 0

RUN apt-get -y update && apt-get -y install curl=7.47.0-1ubuntu2.7

# install chef-solo
RUN curl -L  https://www.opscode.com/chef/install.sh | bash

# install java
RUN apt-get -y update && apt-get -y install default-jre
