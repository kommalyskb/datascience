# Using the official docker image

Use this command to launch Apache Zeppelin in a container.
```
docker run -d -p 8081:8080 --rm --name zeppelin apache/zeppelin:0.10.0
```

To persist logs and notebook directories, use the volume option for docker container.
```
docker run -u $(id -u) -p 8080:8080 --rm -v $PWD/logs:/logs -v $PWD/notebook:/notebook \
           -e ZEPPELIN_LOG_DIR='/logs' -e ZEPPELIN_NOTEBOOK_DIR='/notebook' \
           --name zeppelin apache/zeppelin:0.10.0
```

-u $(id -u) is to make sure you have the permission to write logs and notebooks.

For many interpreters, they require other dependencies, e.g. Spark interpreter requires Spark binary distribution and Flink interpreter requires Flink binary distribution. You can also mount them via docker volumn. e.g.

```
docker run -u $(id -u) -p 8080:8080 --rm -v /mnt/disk1/notebook:/notebook \
-v /usr/lib/spark-current:/opt/spark -v /mnt/disk1/flink-1.12.2:/opt/flink -e FLINK_HOME=/opt/flink  \
-e SPARK_HOME=/opt/spark  -e ZEPPELIN_NOTEBOOK_DIR='/notebook' --name zeppelin apache/zeppelin:0.10.0
```
