FROM tomcat:8

# Install JDK8 Maven
RUN apt-get update 
RUN apt-get upgrade -y 
RUN apt-get install openjdk-8-jdk maven -y

# Delete the default WebApps
RUN rm -Rf webapps/*

# Improve Startup Speed
COPY conf conf

# Set sakai.properties
COPY sakai sakai

# Download and extract Sakai
ADD sakai-11.4.tar.gz /sakai-source/ 

#Install Sakai
WORKDIR /sakai-source/sakai-11.4/
RUN mvn clean install sakai:deploy -DskipTests=true -Dmaven.javadoc.skip=true -Dmaven.tomcat.home=$CATALINA_HOME
WORKDIR $CATALINA_HOME

EXPOSE 8080
CMD ["catalina.sh", "run"]
