# Build stage - Using verified available Maven image
FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn package -DskipTests

# Run stage - Using verified Tomcat image
FROM tomcat:10.1.24-jdk21-temurin-jammy
WORKDIR /usr/local/tomcat/webapps
RUN rm -rf /usr/local/tomcat/webapps/*

# Correct path to WAR file (note: /app/target/ from build stage)
COPY --from=build /app/target/bank-project.war ./ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
