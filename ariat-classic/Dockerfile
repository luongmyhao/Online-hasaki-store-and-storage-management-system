# Giai đoạn build
FROM maven:3.8.5-openjdk-17 AS build

# Chuyển đến đúng thư mục chứa pom.xml trong repo
WORKDIR /app

# Chỉ copy phần thư mục chứa pom.xml (đúng tên thư mục con)
COPY "ariat-classic" .

RUN mvn clean package -DskipTests

# Giai đoạn chạy
FROM openjdk:17-jdk-slim

WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]

