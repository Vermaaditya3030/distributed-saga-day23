FROM maven:3.9.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY orchestrator-service/pom.xml orchestrator-service/pom.xml
COPY orchestrator-service/src orchestrator-service/src
RUN mvn -q -pl orchestrator-service -am package -DskipTests
FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=build /app/orchestrator-service/target/orchestrator-service-1.0.0.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
