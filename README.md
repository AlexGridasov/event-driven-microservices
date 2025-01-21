# event-driven-microservices

# Running the application
- Please enter the correct credentials in twitter4j.properties file.
- Then run `mvn clean install -DskipTests` command
- Then run TwitterToKafkaServiceApplication inside IntelliJ, or run with mvn spring-boot:run command
- Then go to docker-compose folder and run `docker-compose up` command to run kafka cluster, config-server and twitter-to-kafka-service

To run kafka cluster
```
docker-compose up
docker-compose -f common.yml -f kafka_cluster.yml up
docker-compose -f common.yml -f services.yml up
```

Check containers
```
docker ps
```

Check logs
```
docker logs <id>
docker logs -f <id>
```

Check Kafka
```
kafkacat -L -b localhost:19092
kcat -L -b localhost:19092
```

Kafkacat consume
```
kafkacat -C -b localhost:19092 -t twitter-topic
kcat -C -b localhost:19092 -t twitter-topic
```
