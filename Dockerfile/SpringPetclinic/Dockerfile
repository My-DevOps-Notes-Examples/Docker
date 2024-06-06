FROM amazoncorretto:17
LABEL author="nagasuribabukola" organization="techsolutions" project="learning"
RUN curl https://khajareferenceapps.s3.ap-south-1.amazonaws.com/spring-petclinic-3.2.0-SNAPSHOT.jar -o spring-petclinic-3.2.0.jar
EXPOSE 8080
CMD ["java", "-jar", "spring-petclinic-3.2.0.jar"]