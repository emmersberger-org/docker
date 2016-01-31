# activeMQ
#
# Version ActiveMQ5

FROM cemmersb/centos-jdk8

MAINTAINER Christoph Emmersberger, cemmersb@gmail.com

ENV ACTIVEMQ_VERSION 5.13.0
ENV ACTIVEMQ apache-activemq-$ACTIVEMQ_VERSION
ENV ACTIVEMQ_HOME /opt/activemq

RUN \
    curl -O http://archive.apache.org/dist/activemq/$ACTIVEMQ_VERSION/$ACTIVEMQ-bin.tar.gz && \
    tar xf $ACTIVEMQ-bin.tar.gz -C /opt/ && \
    rm $ACTIVEMQ-bin.tar.gz && \
    ln -s /opt/$ACTIVEMQ $ACTIVEMQ_HOME && \
    useradd -r -M -d $ACTIVEMQ_HOME activemq && \
    chown activemq:activemq /opt/$ACTIVEMQ -R

USER activemq

WORKDIR $ACTIVEMQ_HOME
EXPOSE 61616 8161

CMD ["/bin/bash", "-c", "bin/activemq console"]
