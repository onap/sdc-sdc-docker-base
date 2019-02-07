FROM jetty:9.4-jre8-alpine

USER root


# Install Chef
RUN set -ex && \
    apk add --no-cache \
        jq \
        curl \
        curl-dev \
        libressl-dev \
        vim=8.1.0115-r0 \
        bash \
        build-base \
        ruby=2.5.2-r0 \
        ruby-dev \
        libffi-dev \
        libxml2-dev

RUN gem install berkshelf:6.3.1 --no-rdoc --no-ri
RUN gem install io-console:0.4.6 --no-rdoc --no-ri
RUN gem install etc webrick --no-rdoc --no-ri && \
    apk add --no-cache binutils jq libtasn1
RUN gem install chef:13.8.5 --no-rdoc --no-ri
# Replace Jetty user ID
COPY set_jetty_user.sh /tmp/set_jetty_user.sh
RUN sh -x /tmp/set_jetty_user.sh && rm -f /tmp/set_jetty_user.sh && chown -R jetty:jetty ${JETTY_BASE}/webapps /var/lib/jetty

USER jetty
