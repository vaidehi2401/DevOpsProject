# Stage 1: Build
FROM maven:3.9-eclipse-temurin-17-alpine AS build

WORKDIR /app
# copy only pom first to cache dependencies
COPY pom.xml . 
RUN mvn dependency:go-offline -B

# copy sources and build
COPY src ./src
RUN mvn -B clean package -DskipTests

# Stage 2: Run
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app
# change the jar name below if your artifactId/version differ
COPY --from=build /app/target/emp_backend-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080
ENV SPRING_PROFILES_ACTIVE=prod
ENTRYPOINT ["java", "-jar", "app.jar"]

