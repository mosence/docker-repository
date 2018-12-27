FROM openjdk:8-jdk-alpine3.8
ARG JANUSGRAPH_VERSION=0.3.1
RUN apk add unzip -y
RUN adduser janusgraph -D -S
USER janusgraph
WORKDIR /home/janusgraph
RUN \
	wget https://github.com/JanusGraph/janusgraph/releases/download/v$JANUSGRAPH_VERSION/janusgraph-$JANUSGRAPH_VERSION-hadoop2.zip &&\
	unzip janusgraph-$JANUSGRAPH_VERSION-hadoop2.zip -d /home/janusgraph/ &&\
	rm -f janusgraph-$JANUSGRAPH_VERSION-hadoop2.zip &&\
	mv -f ./janusgraph-$JANUSGRAPH_VERSION-hadoop2/* ./ &&\
	rm -rf janusgraph-$JANUSGRAPH_VERSION-hadoop2
EXPOSE 8182
VOLUME ["/home/janusgraph/data"]
CMD ["/bin/bash","-c","bin/janusgraph.sh -v start&&tailf log/*"]