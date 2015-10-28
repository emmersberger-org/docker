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
COPY bin/activemq /usr/activemq/bin/activemq
RUN chmod 755 /usr/activemq/bin/activemq

# Add activemq user
RUN useradd -M activemq -d /usr/activemq
RUN chown -R activemq:users /usr/activemq

# Configure data folder
RUN mkdir -p /var/local/activemq
RUN chown -R activemq:users /var/local/activemq

# Configure logging folder
RUN mkdir -p /var/log/activemq/
RUN chown -R activemq:users /var/log/activemq
COPY conf/log4j.properties /usr/activemq/conf/log4j.properties

# Expose the required ports
EXPOSE 61616 8161

# Configure UNIX Service
COPY bin/env /etc/default/activemq
RUN chmod 644 /etc/default/activemq
RUN ln -snf  /usr/activemq/bin/activemq /etc/init.d/activemq
RUN chkconfig --add activemq
COPY etc/profile.d/activemq.sh /etc/profile.d/activemq.sh
