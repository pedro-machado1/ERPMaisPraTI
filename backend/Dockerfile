#Estágio 1: build 
FROM eclipse-temurin:17-jdk AS build

WORKDIR /build

# Copia o Maven wrapper e o pom.xml primeiro
COPY .mvn/ .mvn/
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline -q

# Copia o código-fonte e compila
COPY src/ src/
RUN ./mvnw package -DskipTests -q

# runtime 
FROM eclipse-temurin:17-jre

WORKDIR /api-erp

EXPOSE 8080

COPY --from=build /build/target/maisPraTi-0.0.1-SNAPSHOT.jar api-erp.jar

ENTRYPOINT ["java", "-jar", "api-erp.jar"]
