FROM openjdk:8-jre-alpine
VOLUME /tmp

# Download dockerize and cache that layer
ADD dockerize/dockerize-alpine-linux-amd64-v0.6.1/dockerize dockerize
RUN chmod +x dockerize

# This is the first layer that won't be cached
ARG ARTIFACT_NAME
ADD ${ARTIFACT_NAME}.jar /app.jar

ARG EXPOSED_PORT
EXPOSE ${EXPOSED_PORT}

ENV SPRING_PROFILES_ACTIVE docker

ENTRYPOINT ["java", "-XX:+UnlockExperimentalVMOptions", "-XX:+UseCGroupMemoryLimitForHeap", "-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
