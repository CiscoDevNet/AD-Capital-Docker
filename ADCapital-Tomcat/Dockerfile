FROM tomcat:9-jre8

RUN apt-get update && \
    apt-get upgrade -y

ENV DOCKERIZE_VERSION v0.5.0

RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

# Shared directory mounted as docker volume
ENV PROJECT /project

ENV GRADLE_HOME $PROJECT/gradle-2.1
ENV PATH $PATH:$GRADLE_HOME/bin

ADD startup.sh /
RUN chmod 744 /startup.sh

# Note: This command should not return or the container will exit
CMD "/startup.sh"

EXPOSE 80
EXPOSE 8080
EXPOSE 8009
