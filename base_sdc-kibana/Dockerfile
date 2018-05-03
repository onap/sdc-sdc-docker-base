FROM kibana:4.3.3

RUN apt-get -y update && apt-get -y install \
    curl=7.38.0-4+deb8u10 \
    vim=2:7.4.488-7+deb8u3

# install chef-solo
RUN curl -L https://omnitruck.chef.io/install.sh | bash

