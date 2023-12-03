FROM openjdk:8-jdk-alpine

LABEL maintainer="Wagner Franchin"

RUN apk update && apk add ca-certificates wget && update-ca-certificates

COPY . .

# ADD /var/jenkins_home/.m2/repository/com/mycompany/spring-rest-mysql/0.0.1-SNAPSHOT/spring-rest-mysql-0.0.1-SNAPSHOT.jar /spring-rest-mysql.jar

CMD ["java", "-jar", "/spring-rest-mysql.jar"]
