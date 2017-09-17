FROM tomcat:8

# Delete the default WebApps
RUN rm -Rf webapps/*

# Improve Startup Speed
COPY conf conf

# Set sakai.properties
COPY sakai sakai

# Download and extract Sakai
ADD http://source.sakaiproject.org/release/11.2/artifacts/sakai-bin-11.2.tar.gz . 

EXPOSE 8080
CMD ["catalina.sh", "run"]
