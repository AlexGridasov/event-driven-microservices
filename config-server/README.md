# Running the application
- run `mvn clean install -DskipTests` command
- set `CONFIG_DIR_PATH` and `SECRET_KEY` environment variables
- run service
- open `http://localhost:8888/config-client/twitter_to_kafka`

To build image
```
docker build -t microservices.demo/config-server:0.0.1-SNAPSHOT .
```

To run
```
docker run -p 8888:8888 \
  -v ../config-server-repository:/config-dir \
  --env ENCRYPT_KEY=encrypt-secret \
  --env CONFIG_DIR_PATH=config-dir \
  microservices.demo/config-server:0.0.1-SNAPSHOT
```
