FROM openjdk:8-jdk-alpine

LABEL maintainer="Wagner Franchin"

RUN apk update && apk add ca-certificates wget && update-ca-certificates

ADD spring-mvc-test-0.0.1-SNAPSHOT.jar /spring-mvc-test.jar

CMD ["java", "-jar", "/spring-rest-mysql.jar"]
