# syntax = docker/dockerfile:1.0-experimental
FROM maven:3.3.3-jdk-8 as builder

WORKDIR /build
COPY ./pom.xml .
COPY ./src/ /build/src/
RUN --mount=type=cache,target=/root/.m2 \
    mvn clean package

FROM openjdk:8-alpine
COPY --from=builder /build/target/*.jar /app/libs/
COPY --from=builder /build/src/main/resources/* /app/resources/
CMD java -cp /app/resources -DISUCON5_DB_PASSWORD=root -DISUCON5_DB_HOST=host.docker.internal -DISUCON5_DB_PORT=3307 -DISUCON5_DB_NAME=isucon5q -jar app/libs/isuxi-0.0.1-SNAPSHOT.jar
