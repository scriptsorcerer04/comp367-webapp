# Use the official Maven image as a parent image
FROM maven:3.8.4-openjdk-17-slim AS build

# Set the working directory in the container
WORKDIR /app

# Copy the Maven POM file and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline -e

# Copy the rest of the application source code
COPY src src

# Expose the port that the Jetty server will be listening on
EXPOSE 8080

# Start the Jetty server using mvn jetty:run
CMD ["mvn", "jetty:run"]
