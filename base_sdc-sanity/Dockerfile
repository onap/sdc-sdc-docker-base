FROM openjdk:8-jdk-alpine

# Install Chef
RUN set -ex && \
    apk add --no-cache \
    curl \
    vim \
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
    apk add binutils curl libcurl libtasn1
