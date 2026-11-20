
# Build stage
FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /app

COPY . .

RUN chmod +x mvnw && ./mvnw -B -DskipTests clean package

# Run stage
FROM eclipse-temurin:17-jre

WORKDIR /app

COPY --from=build /app/target/doctorbooking-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

CMD ["sh", "-c", "java -jar app.jar"]
