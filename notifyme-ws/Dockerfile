# Dockerfile for NotifyMe-WS
# http://www.ubique.ch/

FROM openjdk:11.0.7-jre-buster
MAINTAINER Martin Alig <alig@ubique.ch>
MAINTAINER Felix Haller <haller@ubique.ch>
MAINTAINER Fabian Aggeler <aggeler@ubique.ch>


# Install ws
RUN useradd ws

WORKDIR /home/ws/

# Copy configs
COPY ./ws /home/ws

# Create skeleton
RUN mkdir -p /home/ws/bin && \
    mkdir -p /home/ws/archive && \
    mkdir -p /home/ws/log && \
    mkdir -p /home/ws/tmp

# Copy binary
COPY ./ws/bin/notifyme-sdk-backend-ws-1.0.0.jar /home/ws/bin/notifyme-sdk-backend-ws.jar

RUN chown -R ws:ws /home/ws

USER ws
# Access to webinterface
EXPOSE 8080

CMD java -jar $JAVA_OPTS -Dlogging.config=/home/ws/conf/notifyme-sdk-backend-ws-logback.xml -Dspring.config.location=/home/ws/conf/notifyme-sdk-backend-ws.properties /home/ws/bin/notifyme-sdk-backend-ws.jar
