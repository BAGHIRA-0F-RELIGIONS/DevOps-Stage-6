FROM maven:3.8.6-openjdk-11 AS build
WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn package -DskipTests 

FROM amazoncorretto:8
WORKDIR /app

COPY --from=build /app/target/*.jar ./app.jar

EXPOSE 8083

ENTRYPOINT ["java", "-jar", "app.jar"]
