# Run Nifi on Docker
Ref: https://javahelps.com/how-to-run-apache-nifi-on-docker

## Spin Up Apache NiFi on Docker
```
docker pull apache/nifi:1.19.0
```

```
docker run --name nifi -p 8443:8443 -e NIFI_WEB_HTTPS_PORT='8443' -d apache/nifi:1.19.0
```

## Extract the Credentials from Logs
```
docker logs -f nifi
```
Look for the following line to get the port Apache NiFi is running.
```
INFO [main] org.apache.nifi.web.server.JettyServer https://4cdc79d1487f:8443/nifi
Generated Username [xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx]
Generated Password [xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx]
```
To start NiFi with your own username and password, use the following command instead:
```
docker run --name nifi -p 8443:8443 -e SINGLE_USER_CREDENTIALS_USERNAME=admin -e SINGLE_USER_CREDENTIALS_PASSWORD=ctsBtRBKHRAx69EqUghvvgEvjnaLjFEB -d apache/nifi:1.19.0
```

# Run NiFi Cluster in Docker with SSL Enabled
Ref: https://javahelps.com/run-nifi-cluster-in-docker-with-ssl-enabled