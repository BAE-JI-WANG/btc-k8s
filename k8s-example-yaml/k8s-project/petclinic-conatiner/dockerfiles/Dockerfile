FROM openjdk:18
ADD spring-petclinic.tar /
WORKDIR /spring-petclinic
RUN ./mvnw package -DskipTests=true
EXPOSE 8080/TCP
CMD ["java", "-jar", "target/*.jar"]
