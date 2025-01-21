# config-server

Run the application with `--spring.profiles.active=default` if you know the Config Server won't be available.

To build image
```
docker build -t microservices.demo/twitter-to-kafka-service:0.0.1-SNAPSHOT .
```

To run
```
docker run -p 8080:8080 \
  --env ENCRYPT_KEY=encrypt-secret \
  --env SPRING_CLOUD_CONFIG_URI=http://localhost:8888 \
  microservices.demo/twitter-to-kafka-service:0.0.1-SNAPSHOT
```
