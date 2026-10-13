# Packages a prebuilt Spring Boot jar; run `mvn package` before building.
FROM eclipse-temurin:17-jre

ARG SERVICE
RUN test -n "$SERVICE" || (echo "SERVICE build arg is required" && exit 1)

RUN groupadd --system app && useradd --system --gid app --no-create-home app
WORKDIR /app

COPY services/${SERVICE}/target/${SERVICE}-*.jar /app/app.jar

USER app
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
