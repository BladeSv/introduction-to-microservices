FROM amazoncorretto:17 as build_docker
RUN mkdir -p /project
COPY . /project
WORKDIR /project
RUN ./gradlew clean bootJar && cp ./build/libs/registration-service-0.0.1-SNAPSHOT.jar registration-service.jar

FROM amazoncorretto:17
COPY --from=build_docker /project/registration-service.jar registration-service.jar
CMD ["java", "-jar", "registration-service.jar"]