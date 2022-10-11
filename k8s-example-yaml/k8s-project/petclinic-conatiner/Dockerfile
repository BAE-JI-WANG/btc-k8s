FROM openjdk:18-jdk-alpine AS builder
ADD spring-petclinic.tar /
WORKDIR /spring-petclinic
RUN ./mvnw spring-javaformat:apply
RUN ./mvnw package

FROM openjdk:18-jdk-alpine
COPY --from=builder /spring-petclinic/target/spring-petclinic-2.7.0-SNAPSHOT.jar /svc/app/bin/spring-petclinic-2.7.0-SNAPSHOT.jar

EXPOSE 8080/TCP 8009/TCP

CMD ["java", "-jar","-Dspring.profiles.active='mysql'", "/svc/app/bin/spring-petclinic-2.7.0-SNAPSHOT.jar"]