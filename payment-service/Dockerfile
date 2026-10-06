FROM maven:3.9.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY payment-service/pom.xml payment-service/pom.xml
COPY payment-service/src payment-service/src
RUN mvn -q -pl payment-service -am package -DskipTests
FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=build /app/payment-service/target/payment-service-1.0.0.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
