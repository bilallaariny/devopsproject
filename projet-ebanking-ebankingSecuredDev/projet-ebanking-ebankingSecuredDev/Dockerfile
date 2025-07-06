# Build stage
FROM maven:3.8.4-openjdk-17 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn package -DskipTests

# Run stage
FROM tomcat:9.0-jdk17-openjdk-slim
WORKDIR /app

## Copy the WAR file to Tomcat's webapps directory
#COPY --from=build /app/target/backend-0.0.1-SNAPSHOT.war /usr/local/tomcat/webapps/ROOT.war

# Alternative if you want to keep the original filename:
 COPY --from=build /app/target/bank-project.war /usr/local/tomcat/webapps/backend.war

# Expose port 8080 (Tomcat's default)
EXPOSE 8080



# Tomcat will automatically deploy the WAR file on startup
CMD ["catalina.sh", "run"]