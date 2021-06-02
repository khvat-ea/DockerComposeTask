FROM maven:3.8.1-jdk-11

# Building a java-war application
WORKDIR /tmp
RUN git clone https://github.com/boxfuse/boxfuse-sample-java-war-hello.git
WORKDIR /tmp/boxfuse-sample-java-war-hello
RUN mvn package

ENTRYPOINT [ "/bin/sh", "-c", "exit 0" ]