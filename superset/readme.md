# Start a superset instance on port 8088

```
docker run -d -p 8088:8088 --name superset apache/superset
```

# Initialize a local Superset Instance

Setup your local admin account
```
docker exec -it superset superset fab create-admin --username admin --firstname Superset --lastname Admin --email admin@superset.com --password admin
```
Migrate local DB to latest
```
docker exec -it superset superset db upgrade
```
Load Examples
```
docker exec -it superset superset load_examples
```
Setup roles
```
docker exec -it superset superset init
```