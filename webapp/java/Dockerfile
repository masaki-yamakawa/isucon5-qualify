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
CMD java -cp /app/resources \
      -DISUCON5_DB_HOST=${ISUCON5_DB_HOST} \
      -DISUCON5_DB_PORT=${ISUCON5_DB_PORT} \
      -DISUCON5_DB_NAME=${ISUCON5_DB_NAME} \
      -DISUCON5_DB_USER=${ISUCON5_DB_USER} \
      -DISUCON5_DB_PASSWORD=${ISUCON5_DB_PASSWORD} \
      -jar app/libs/isuxi-0.0.1-SNAPSHOT.jar
