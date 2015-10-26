# activeMQ
#
# Version ActiveMQ5

FROM cemmersb/centos-jdk8

MAINTAINER Christoph Emmersberger, cemmersb@gmail.com

ENV ACTIVEMQ_VERSION 5.12.1

RUN yum -y upgrade

# Download, extract and move activemq to final destination
RUN wget "https://repository.apache.org/content/repositories/releases/org/apache/activemq/apache-activemq/$ACTIVEMQ_VERSION/apache-activemq-$ACTIVEMQ_VERSION-bin.tar.gz" -O /tmp/apache-activemq-$ACTIVEMQ_VERSION-bin.tar.gz
RUN tar xvfz /tmp/apache-activemq-$ACTIVEMQ_VERSION-bin.tar.gz -C /usr/
RUN mv /usr/apache-activemq-$ACTIVEMQ_VERSION /usr/activemq
RUN rm /tmp/apache-activemq-$ACTIVEMQ_VERSION-bin.tar.gz
