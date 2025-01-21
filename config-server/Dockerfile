# Layered Jars
FROM openjdk:11-jre-slim-buster AS jar_extract
WORKDIR /app
ARG JAR_FILE=config-server-*.jar
COPY ./target/${JAR_FILE} ./app.jar
RUN java -Djarmode=layertools -jar ./app.jar extract

FROM openjdk:11-jre-slim-buster
# Install curl
RUN apt-get update && apt-get install -y --no-install-recommends curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
WORKDIR /application
COPY --from=jar_extract /app/dependencies ./
COPY --from=jar_extract /app/spring-boot-loader ./
COPY --from=jar_extract /app/snapshot-dependencies ./
COPY --from=jar_extract /app/application ./
ENTRYPOINT ["java", "org.springframework.boot.loader.JarLauncher"]
