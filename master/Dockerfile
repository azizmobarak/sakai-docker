FROM maven:3-jdk-8 as builder
WORKDIR /

ADD https://github.com/azizmobarak/sakai/archive/master.zip /master.zip
RUN unzip master.zip
WORKDIR /sakai-master
RUN mvn clean install sakai:deploy -Dmaven.tomcat.home=/sakai-tomcat-output -DskipTests=true


FROM tomcat:9-jre8 as app
WORKDIR $CATALINA_HOME
EXPOSE 8080

COPY ./conf ./conf
COPY ./lib ./lib
COPY ./sakai ./sakai
RUN rm -rf ./webapps/*
COPY --from=builder /sakai-tomcat-output ./
CMD ["catalina.sh", "run"]
