FROM alpine:3.8

# add our user and group first to make sure their IDs get assigned consistently
RUN addgroup -S kibana && adduser -S -G kibana kibana

RUN apk add --no-cache \
#		apt-transport-https \
		ca-certificates \
		wget \
		gnupg \
		nodejs \
		tini \
# generating PDFs requires libfontconfig and libfreetype6, alpine doesn't have the libs, testing these installs
		fontconfig \
		freetype \
;

ENV KIBANA_VERSION 4.3.3
#ENV KIBANA_TARBALL="https://artifacts.elastic.co/downloads/kibana/kibana-${KIBANA_VERSION}-linux-x86_64.tar.gz"
ENV KIBANA_TARBALL="https://download.elastic.co/kibana/kibana/kibana-${KIBANA_VERSION}-linux-x64.tar.gz"
#ENV KIBANA_TARBALL_SHA1="$(curl https://download.elastic.co/kibana/kibana/kibana-${KIBANA_VERSION}-linux-x64.tar.gz.sha1.txt)" 

WORKDIR /usr/share/kibana

RUN wget -O kibana.tar.gz "$KIBANA_TARBALL"; \
        \
        if [ "$KIBANA_TARBALL_SHA1" ]; then \
                echo "$KIBANA_TARBALL_SHA1 *kibana.tar.gz" | sha1sum -c -; \
        fi; \
	\
	tar -xf kibana.tar.gz --strip-components=1 && \
	mkdir -p /usr/share/kibana/node/bin && \
	ln -sf /usr/bin/node /usr/share/kibana/node/bin/node && \
        rm kibana.tar.gz && \
	\
# the default "server.host" is "localhost" in 5+
	sed -ri "s!^(\#\s*)?(server\.host:).*!\2 '0.0.0.0'!" /usr/share/kibana/config/kibana.yml \
	&& grep -q "^server\.host: '0.0.0.0'\$" /usr/share/kibana/config/kibana.yml \
	\
# ensure the default configuration is useful when using --link
	&& sed -ri "s!^(\#\s*)?(elasticsearch\.url:).*!\2 'http://elasticsearch:9200'!" /usr/share/kibana/config/kibana.yml \
	&& grep -q "^elasticsearch\.url: 'http://elasticsearch:9200'\$" /usr/share/kibana/config/kibana.yml

RUN chmod 777 optimize
ENV PATH /usr/share/kibana/bin:$PATH
USER kibana
ENTRYPOINT ["tini"]
EXPOSE 5601
CMD ["kibana"]
