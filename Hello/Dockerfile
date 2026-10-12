FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

COPY build/libs/Hello-0.0.1-SNAPSHOT.jar app.jar

RUN addgroup -S app && adduser -S -G app app

ENV PORT=3000

EXPOSE 3000

USER app

CMD ["java", "-jar", "app.jar"]
