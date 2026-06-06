# Stage 1: Downloading corresponding server jar GitHub
FROM alpine:latest AS downloader
ARG BTA_VERSION
RUN apk add --no-cache curl

WORKDIR /download

RUN curl -L -o bta-server.jar "https://github.com/USER/REPO/releases/download/${BTA_VERSION}/bta.${BTA_VERSION}.server.jar"

# Stage 2: Running installed BTA server jar
FROM eclipse-temurin:8-jre-alpine
WORKDIR /app

COPY --from=downloader /download/bta-server.jar /app/server.jar

RUN echo "eula=true" > eula.txt

EXPOSE 25565

CMD ["java", "-jar", "server.jar", "nogui"]