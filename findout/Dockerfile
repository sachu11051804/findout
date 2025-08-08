# Use official Tomcat 10.1 with Java 17 (Temurin JDK)
FROM tomcat:10.1-jdk17-temurin

# Remove default web apps to keep image clean
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy your WAR file into Tomcat as ROOT.war
COPY ROOT.war /usr/local/tomcat/webapps/ROOT.war

# Download json-simple-1.1.jar directly into Tomcat's lib folder
RUN curl -L -o /usr/local/tomcat/lib/json-simple-1.1.jar \
    https://repo1.maven.org/maven2/com/googlecode/json-simple/json-simple/1.1/json-simple-1.1.jar

# Environment variables for all APIs (can override at runtime with -e)
ENV ABSTRACT_EMAIL_API_KEY=34cbe738bb7348b78089ae649f5f045d \
    ABSTRACT_PHONE_API_KEY=eac57b41579e4bce95e2de2686d6a72d \
    ABSTRACT_COMPANY_API_KEY=9d1ff2f986924dba81db6c31b64b4612 \
    IPINFO_API_KEY=88cc1d55b1119a

# Optional: Disable Tomcat shutdown port for security
RUN sed -i 's/<Server port="8005"/<Server port="-1"/' /usr/local/tomcat/conf/server.xml

# Expose Tomcat HTTP port
EXPOSE 8080

# Start Tomcat
CMD ["catalina.sh", "run"]

