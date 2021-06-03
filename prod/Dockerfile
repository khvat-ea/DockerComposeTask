  
FROM alpine:3.7

# Preparing the environment for deployment
RUN apk update \
    && apk install build-essential wget default-jdk \
    && wget http://apache.rediris.es/tomcat/tomcat-9/v9.0.46/bin/apache-tomcat-9.0.46.tar.gz -O /tmp/tomcat9.tar.gz \
    && tar -C "/opt" -xvf /tmp/tomcat9.tar.gz 

ENV JAVA_HOME /usr/lib/jvm/java-1.11.0-openjdk-amd64
ENV CATALINA_HOME /opt/apache-tomcat-9.0.46

# Deploying Tomcat
# According to instructions https://tomcat.apache.org/tomcat-9.0-doc/setup.html
RUN useradd -r tomcat \
    && cd $CATALINA_HOME/bin \
    && tar xvfz commons-daemon-native.tar.gz \
    && cd commons-daemon-1.2.4-native-src/unix \
    && ./configure \
    && make \
    && cp jsvc ../..

# Container launch conditions
EXPOSE 8080
CMD $CATALINA_HOME/bin/daemon.sh run