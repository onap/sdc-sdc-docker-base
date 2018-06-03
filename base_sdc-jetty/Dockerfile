FROM jetty:9.3-jre8-alpine

USER root


# Install Chef
RUN set -ex && \
    apk add --no-cache \
        jq=1.5-r5 \
        curl=7.60.0-r1 \
        curl-dev=7.60.0-r1 \
        openssl-dev=1.0.2o-r0 \
        vim=8.0.1359-r0 \
        bash=4.4.19-r1 \
        build-base=0.5-r0 \
        ruby=2.4.4-r0 \
        ruby-dev=2.4.4-r0 \
        libffi-dev=3.2.1-r4 \
        libxml2-dev=2.9.7-r0 && \
    gem install \
        chef:13.8.5 \
        berkshelf:6.3.1 \
        io-console:0.4.6 \
        --no-document && \
    echo "http://nl.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories && \
    apk update && \
    apk add binutils=2.30-r1 jq=1.6_rc1-r1 libtasn1=4.13-r0

# Replace Jetty user ID
COPY set_jetty_user.sh /tmp/set_jetty_user.sh
RUN sh -x /tmp/set_jetty_user.sh && rm -f /tmp/set_jetty_user.sh
RUN chown -R jetty:jetty ${JETTY_BASE}/webapps /var/lib/jetty

USER jetty

