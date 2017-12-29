FROM tomcat:8

# Delete the default WebApps
RUN rm -Rf webapps/**/*

# COPY http://source.sakaiproject.org/release/11.0/artifacts/sakai-bin-11.0.zip
COPY ./components/ ./components/
COPY ./lib/ ./lib/
COPY ./licenses/ ./licenses/
COPY ./webapps/ ./webapps/

# Improve Startup Speed
COPY ./conf/ ./conf/

# Set sakai.properties
COPY ./sakai/ ./sakai/

EXPOSE 8080
CMD ["catalina.sh", "run"]
