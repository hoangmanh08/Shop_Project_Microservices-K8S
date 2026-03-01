# Stage 1: Build the application
FROM eclipse-temurin:17-jdk-jammy AS builder

WORKDIR /app
COPY . .
# cấp quyền chạy cho mvnw
RUN chmod +x mvnw
RUN ./mvnw clean package -DskipTests

# Stage 2: Run the application
FROM eclipse-temurin:17-jdk-jammy

WORKDIR /app
COPY --from=builder /app/target/discovery-server-0.0.1-SNAPSHOT.war /app/discovery-server.war

CMD ["java", "-jar", "discovery-server.war"]
