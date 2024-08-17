FROM alpine/git AS code
RUN cd / && git clone https://github.com/wakaleo/game-of-life.git

FROM maven:3.6.3-jdk-8 AS builder
COPY --from=code /game-of-life /game-of-life
RUN cd /game-of-life && mvn package

FROM tomcat:9-jdk8
LABEL author="suresh"   purpose="learning"
COPY --from=builder /game-of-life/**/target/*.war /usr/local/tomcat/webapps/gameoflife.war
EXPOSE 8080