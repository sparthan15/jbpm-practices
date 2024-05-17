## JBPM with docker
https://www.jbpm.org/learn/gettingStartedUsingDocker.html
## how to run
We could use postgresql for persistence, so there is a standalont-postgresql which has the config for that. change the docker-compose.yml accordingly.
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
docker run -8080:8080 -p8001:8001 --name jbpm-server-full jboss/jbpm-server-full:latest
```
## Deleting volumes
```
docker-compose down
rm -rf ./volumes/db 
docker-compose build
docker-compose up -d
```
## Cloning a project
You are able to clone projects, by running 