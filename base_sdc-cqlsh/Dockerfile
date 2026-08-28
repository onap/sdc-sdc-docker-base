FROM openjdk:8-jdk-alpine

RUN addgroup -g 1000 sdc && adduser -S -u 1000 -G sdc -s /bin/sh sdc
USER sdc
RUN mkdir ~/.cassandra/ && \
    echo  '[cql]' > ~/.cassandra/cqlshrc  && \
    echo  'version=3.4.4' >> ~/.cassandra/cqlshrc 
USER root

RUN apk add --no-cache py-pip && \
    pip install --no-cache-dir cqlsh==5.0.4 && \
    mkdir ~/.cassandra/ && \
    echo  '[cql]' > ~/.cassandra/cqlshrc  && \
    echo  'version=3.4.4' >> ~/.cassandra/cqlshrc  && \
    set -ex && \
    pip install --no-cache-dir cqlsh && \
    apk add --no-cache \
    bash \
    build-base \
    ruby=2.5.8-r0 \
    ruby-dev \
    libffi-dev \
    libxml2-dev && \
    # The bundled RubyGems ignores required_ruby_version and resolves
    # chef's open-ended deps to releases needing Ruby 3.2; 3.3.26 is
    # the last RubyGems supporting this Ruby.
    gem update --system 3.3.26 --no-document && \
    gem install chef:13.8.5 berkshelf:6.3.1 io-console:0.4.6 etc webrick --no-document && \
    apk update && \
    apk add binutils \
    libtasn1
USER sdc
