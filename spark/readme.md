# Install Apache spark
Ref: https://www.youtube.com/watch?v=Zr_FqYKC6Qc

Download docker-compose file
```
$ curl -LO https://raw.githubusercontent.com/bitnami/containers/main/bitnami/spark/docker-compose.yml
$ docker-compose up
```

For docker-compose add the variable name and value under the application section in the docker-compose.yml file present in this repository:
```
spark:
  ...
  environment:
    - SPARK_MODE=master
  ...
```

For manual execution add a -e option with each variable and value:
```
docker run -d --name spark \
  --network=spark_network \
  -e SPARK_MODE=master \
  bitnami/spark
```