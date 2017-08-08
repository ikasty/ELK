FROM node:alpine
MAINTAINER ikasty <mail.ikasty@gmail.com>

ENV KIBANA_VERSION="5.5.1-linux-x86"
RUN apk add --update --no-cache --virtual .build ca-certificates wget && \
	wget -q https://artifacts.elastic.co/downloads/kibana/kibana-$KIBANA_VERSION.tar.gz && \
	tar xzf kibana-$KIBANA_VERSION.tar.gz && \
	apk del .build

CMD node kibana-$KIBANA_VERSION/src/cli --elasticsearch.url=${ELS_URL} --server.host=${HOSTNAME}

# docker run -it --rm --link els:els -p 5601:5601 -e ELS_URL=http://els:9200 kibana
