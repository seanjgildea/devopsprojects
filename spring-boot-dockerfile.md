# Spring Boot project in Dockerfile w/ Container deployment

- Create a normal Spring Boot application with at least one REST endpoint you can test
- Execute the following commands to create an image and then deploy to a container 

```
./mvnw package && java -jar target/[app-name-version].jar
```

## Make sure the app works on localhost:8080
## Create a Dockerfile

```
FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
```

## Run the Dockerfile with the following command and tag (-t) the image as such

```
docker build -t spring-boot-example .
```

- This Dockerfile is very simple, just Java and a JAR file. The project JAR file is added to the container as "app.jar" and then executed in the ENTRYPOINT. 
- The array form of the Dockerfile ENTRYPOINT is used so that there is no shell wrapping the java process
- There is a VOLUME pointing to "/tmp" because that is where a Spring Boot application creates working directories for Tomcat by default. 
- The effect is to create a temporary file on your host under "/var/lib/docker" and link it to the container under "/tmp". 
- This step is optional for simple applications, but can be necessary for other Spring Boot applications if they need to actually write in the filesystem.

## Start the image as a service

```
docker container run -d -p 8080:8080 spring-boot-example
```

- Creates the container and detaches it (-d)
- `-p 8080:8080` opens up a port to the app on port 8080 through the bridge adapter to the localhost:8080
- `docker container ls` will show the services that are running
- `docker container stop [container id]` will stop the service

## Start the image in a docker-compose file with environment variable

```
version: '3'

services:
  java:
    image: spring-boot-example
    build: .
    ports: 
      - "8074:8080"
    environment:
      - some.value=Happy Holidays!
```

- `docker-compose up` to start it , `--build` to force rebuilding the image if it's already built
- Load up localhost:8074 in a browser to see the page and injected environment variable

