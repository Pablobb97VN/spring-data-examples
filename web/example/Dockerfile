FROM maven:3.6-jdk-8-alpine AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn -e -B dependency:resolve
COPY src ./src
RUN mvn -e -B package
FROM openjdk:8-jre-alpine
COPY --from=builder /target/spring-data-web-example-2.0.0.BUILD-SNAPSHOT.jar .
CMD ["java", "-jar", "/target/spring-data-web-example-2.0.0.BUILD-SNAPSHOT.jar"]
