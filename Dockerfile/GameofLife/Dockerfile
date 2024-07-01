FROM tomcat:9-jdk8
LABEL author="nagasuribabukola" purpose="practice"
ARG Download_URL=https://khajareferenceapps.s3.ap-south-1.amazonaws.com/gameoflife.war
ADD ${Download_URL} /usr/local/tomcat/webapps/gameoflife.war
VOLUME [ "/usr/local/tomcat" ]
EXPOSE 8080
# Ignoring CMD, as I want Base Image CMD.