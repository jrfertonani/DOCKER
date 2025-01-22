# Estágio de build com OpenJDK 17
FROM maven:3.8.4-openjdk-17-slim AS build

WORKDIR /meu-projeto-docker

COPY pom.xml .
COPY src ./src

RUN mvn clean install

# Estágio final para o contêiner
FROM openjdk:17-jdk-slim

WORKDIR /app

# Copia o JAR gerado do estágio de build para o contêiner
COPY --from=build /meu-projeto-docker/target/backend-0.0.1-SNAPSHOT.jar /app.jar

ENTRYPOINT ["java", "-jar", "/app.jar"]
