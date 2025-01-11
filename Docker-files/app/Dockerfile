
FROM maven:amazoncorretto AS BUILD_IMAGE
RUN install git && git clone https://github.com/WaritCha/DevopsProject.git
RUN cd DevopsProject && git checkout containers && mvn clean install



FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE DevopsProject/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]