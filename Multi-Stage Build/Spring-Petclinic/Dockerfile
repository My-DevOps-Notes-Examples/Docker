FROM alpine/git AS Code
RUN cd / && git clone https://github.com/spring-projects/spring-petclinic.git

FROM maven:3.8.3-openjdk-17 AS Builder
COPY --from=Code /spring-petclinic /spring-petclinic
RUN cd /spring-petclinic && mvn package

FROM amazoncorretto:17-alpine-jdk
LABEL author="suresh"   purpose="learning"
ARG Home_Dir=/SpringPetclinic
WORKDIR ${Home_Dir}
COPY --from=Builder **/target/*.jar ${Home_Dir}/spring-petclinic.jar
EXPOSE 8080
CMD [ "java", "-jar", "spring-petclinic.jar" ]