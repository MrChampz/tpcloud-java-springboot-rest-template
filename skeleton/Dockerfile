FROM maven:3.9.0-eclipse-temurin-17 as builder

COPY . .

RUN mvn -B -DskipTests clean package

##################################################
FROM openjdk:17-jdk-alpine

LABEL org.opencontainers.image.source https://github.com/diebold-xyz/${{values.component_id}}

COPY --from=builder target/*.jar app.jar

EXPOSE ${{values.http_port}}

ENTRYPOINT ["java", "-jar", "/app.jar"]