FROM eclipse-temurin:17-jdk AS build

WORKDIR /build

RUN apt-get update && apt-get install -y maven

COPY pom.xml ./
RUN mvn dependency:go-offline -q

COPY src/ src/
RUN mvn package -DskipTests -q

FROM eclipse-temurin:17-jre

WORKDIR /api-erp
EXPOSE 8080

COPY --from=build /build/target/maisPraTi-0.0.1-SNAPSHOT.jar api-erp.jar

ENTRYPOINT ["java", "-jar", "api-erp.jar"]