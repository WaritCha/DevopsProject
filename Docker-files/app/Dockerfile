

FROM maven:3.9.9-eclipse-temurin-23-alpine AS build_image
RUN apt-get update && apt-get install -y git
RUN git clone https://github.com/WaritCha/DevopsProject.git
RUN cd DevopsProject && git checkout containers && mvn clean install



FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build_image DevopsProject/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]