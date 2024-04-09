# Use the official Maven image as a build stage
FROM maven:3.9.6-openjdk-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package

# Use AdoptOpenJDK image as the runtime stage
FROM adoptopenjdk/openjdk17:alpine
WORKDIR /app
COPY --from=build /app/target/*.war ./app.war
EXPOSE 8080
CMD ["java", "-jar", "app.war"]
