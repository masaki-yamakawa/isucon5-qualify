FROM maven:3.3.3-jdk-8

RUN mkdir -p /isucon5-webapp
COPY . /isucon5-webapp/
WORKDIR /isucon5-webapp

RUN mvn clean package

CMD java -DISUCON5_DB_PASSWORD=root -DISUCON5_DB_HOST=host.docker.internal -DISUCON5_DB_PORT=3307 -DISUCON5_DB_NAME=isucon5q -jar target/isuxi-0.0.1-SNAPSHOT.jar
