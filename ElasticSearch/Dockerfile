FROM openjdk:jre-alpine
MAINTAINER ikasty <mail.ikasty@gmail.com>

ENV ES_JAVA_OPTS="-Xms1g -Xmx1g" ELASTIC_VERSION="5.5.1"
RUN apk add --update --no-cache --virtual .build ca-certificates wget && \
	wget -q https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-$ELASTIC_VERSION.tar.gz && \
	tar xzf elasticsearch-$ELASTIC_VERSION.tar.gz && \
	apk del .build && \
	adduser -S elasticsearch && \
	chmod -R 777 elasticsearch-$ELASTIC_VERSION && \
	echo "transport.host: 127.0.0.1" >> elasticsearch-$ELASTIC_VERSION/config/elasticsearch.yml && \
	echo "http.host: 0.0.0.0" >> elasticsearch-$ELASTIC_VERSION/config/elasticsearch.yml

USER elasticsearch
CMD sh elasticsearch-$ELASTIC_VERSION/bin/elasticsearch -s

# docker run -it --rm --name els -p 9200:9200 -p 9300:9300 elasticsearch sh
