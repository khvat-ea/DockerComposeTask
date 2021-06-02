FROM maven:3.2-onbuild

# Deploying a java-war application
RUN cd /tmp \
    && git clone https://github.com/boxfuse/boxfuse-sample-java-war-hello.git
WORKDIR /tmp/boxfuse-sample-java-war-hello
RUN mvn package
RUN cp target/hello-1.0.war $CATALINA_HOME/webapps/

# Container launch conditions
EXPOSE 8080
CMD $CATALINA_HOME/bin/daemon.sh run