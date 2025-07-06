
# Utilise une image compatible Tomcat 10.1.x et Java 21
FROM tomcat:10.1.34-jdk21
WORKDIR /usr/local/tomcat/webapps
# Supprime les applications par défaut
RUN rm -rf /usr/local/tomcat/webapps/*

# Alternative if you want to keep the original filename:
 COPY --from=build /target/bank-project.war /usr/local/tomcat/webapps/backend.war

# Expose port 8080 (Tomcat's default)
EXPOSE 8080



# Tomcat will automatically deploy the WAR file on startup
CMD ["catalina.sh", "run"]


