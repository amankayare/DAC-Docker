FROM ubuntu:18.04

# Install Jdk
RUN apt-get update && \
    apt-get install -y openjdk-8-jdk && \
    apt-get install -y ant && \
    apt-get clean
RUN java -version

# Install Apache Tomcat
RUN apt-get install -y  wget && \
        wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.40/bin/apache-tomcat-9.0.40.tar.gz && \
                tar -xvzf apache-tomcat-9.0.40.tar.gz

# Chmod permissions
RUN chmod +x apache-tomcat-9.0.40/bin/startup.sh && \
        chmod +x apache-tomcat-9.0.40/bin/shutdown.sh

# Creating Contex.xml
RUN wget https://final-aws-exam.s3.amazonaws.com/context.xml

# Cp command
RUN cp context.xml apache-tomcat-9.0.40/webapps/manager/META-INF/


# Downloading War
RUN wget https://amankayare-bucket.s3.amazonaws.com/docker/expense-mng-system-0.0.1-SNAPSHOT.war
# Cp command
RUN cp expense-mng-system-0.0.1-SNAPSHOT.war apache-tomcat-9.0.40/webapps

#Run CMD
CMD ["apache-tomcat-9.0.40/bin/catalina.sh", "run"]
EXPOSE 8080

