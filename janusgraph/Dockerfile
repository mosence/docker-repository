FROM openjdk:8-jdk-alpine3.8

MAINTAINER CHANNEL IT SERVICES

ENV JANUSGRAPH_VERSION=0.3.1
RUN apk add unzip -y
RUN adduser janusgraph -D -S -s /bin/bash
RUN \
	su janusgraph &&\
	mkdir /home/janusgraph &&\
	cd /home/janusgraph &&\
	wget https://github.com/JanusGraph/janusgraph/releases/download/v$JANUSGRAPH_VERSION/janusgraph-$JANUSGRAPH_VERSION-hadoop2.zip &&\
	unzip janusgraph-$JANUSGRAPH_VERSION-hadoop2.zip -d /home/janusgraph/janusgraph &&\
	cd /home/janusgraph/janusgraph &&\
	bin/janusgraph.sh -v start
EXPOSE \
	8182 9200 9160 7199