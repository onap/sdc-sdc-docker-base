FROM jetty:9.4.18-jre8-alpine

USER root

# Install Chef
RUN set -ex && \
    apk update && \
    apk add --no-cache \
        jq \
        curl \
        curl-dev \
        libressl-dev \
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
    gem install \
        chef:13.8.5 \
        berkshelf:6.3.1 \
        io-console:0.4.6 \
        etc webrick \
        --no-document && \
    apk update && \
    apk add binutils jq libtasn1

# Replace Jetty user ID
COPY set_jetty_user.sh /tmp/set_jetty_user.sh
RUN sh -x /tmp/set_jetty_user.sh && rm -f /tmp/set_jetty_user.sh && chown -R jetty:jetty ${JETTY_BASE}/webapps /var/lib/jetty

USER jetty
