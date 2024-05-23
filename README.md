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

## Adding a datasource for persisting variables in different DB
You need to add a new xa-datasource to the standalone.xml 
```
<xa-datasource jndi-name="java:jboss/datasources/MatriculaDS" pool-name="jBPMXADS">
                    <xa-datasource-property name="ServerName">
                        postgres
                    </xa-datasource-property>
                    <xa-datasource-property name="PortNumber">
                        5432
                    </xa-datasource-property>
                    <xa-datasource-property name="DatabaseName">
                        proc_escolares_matricula
                    </xa-datasource-property>
                    <xa-datasource-class>org.postgresql.xa.PGXADataSource</xa-datasource-class>
                    <driver>postgres</driver>
                    <security>
                        <user-name>jbpm</user-name>
                        <password>jbpm</password>
                    </security>
                    <validation>
                        <valid-connection-checker class-name="org.jboss.jca.adapters.jdbc.extensions.postgres.PostgreSQLValidConnectionChecker"/>
                        <validate-on-match>true</validate-on-match>
                        <background-validation>true</background-validation>
                        <background-validation-millis>120000</background-validation-millis>
                        <exception-sorter class-name="org.jboss.jca.adapters.jdbc.extensions.postgres.PostgreSQLExceptionSorter"/>
                    </validation>
                </xa-datasource>
```