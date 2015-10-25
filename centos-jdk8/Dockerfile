# java
#
# Version JDK8

FROM centos

MAINTAINER Christoph Emmersberger, cemmersb@gmail.com

ENV JAVA_VERSION 8u65
ENV BUILD_VERSION b17

RUN yum -y upgrade
RUN yum -y install wget

RUN wget --no-cookies --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/$JAVA_VERSION-$BUILD_VERSION/jdk-$JAVA_VERSION-linux-x64.rpm" -O /tmp/jdk-8-linux-x64.rpm

RUN yum -y install /tmp/jdk-8-linux-x64.rpm

RUN alternatives --install /usr/bin/java java /usr/java/latest/bin/java 200000
RUN alternatives --install /usr/bin/javac javac /usr/java/latest/bin/javac 200000

ENV JAVA_HOME /usr/java/latest
