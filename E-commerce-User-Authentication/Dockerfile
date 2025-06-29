# Use Maven image to build the app
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY . /app
WORKDIR /app/E-commerce-User-Authentication
RUN mvn clean package -DskipTests

# Use JDK image to run the app
FROM eclipse-temurin:17-jdk
WORKDIR /app
COPY --from=build /app/E-commerce-User-Authentication/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
