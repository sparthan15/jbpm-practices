## JBPM with docker
## how to run
Loading DB
run 
```
docker-compose up
```
Delete previous container if exists.
```
docker container rm jbpm-server-full
```
Run the container
```
docker run -p9980:8080 -p8001:8001 --name jbpm-server-full jboss/jbpm-server-full:latest
```

## Cloning a project
You are able to clone projects, by running 