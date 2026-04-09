FROM ubuntu:20.04

USER root

RUN apt update -y && \
    apt install -y default-jdk wget && \
    apt clean

WORKDIR /opt/tomcat

# Download Tomcat
RUN wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.117/bin/apache-tomcat-9.0.117.tar.gz

# Extract Tomcat
RUN tar -xvzf apache-tomcat-9.0.117.tar.gz

# Remove tar file (optional)
RUN rm apache-tomcat-9.0.117.tar.gz

# Copy WAR file
ADD https://s3-us-west-2.amazonaws.com/studentapi-cit/student.war /opt/tomcat/apache-tomcat-9.0.117/webapps/

# Copy MySQL connector
ADD https://s3-us-west-2.amazonaws.com/studentapi-cit/mysql-connector.jar /opt/tomcat/apache-tomcat-9.0.117/lib/

# Copy context.xml
COPY context.xml /opt/tomcat/apache-tomcat-9.0.117/conf/context.xml

# Expose Tomcat port
EXPOSE 8080

# Start Tomcat
CMD ["/opt/tomcat/apache-tomcat-9.0.117/bin/catalina.sh", "run"]

