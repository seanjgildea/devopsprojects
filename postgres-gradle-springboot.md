# Sample App with REST 
microservice with a set of simple and internal RESTful APIs that provide ways to create, update and retrieve passes. The microservice is built around a simple Spring Boot application with a PostgreSQL database used for persistence and deployed using Docker.

### Technologies
The technologies used to build this microservice are listed below:
* Gradle
* Spring Boot
* Java 1.8
* [Project Lombok](https://projectlombok.org)
* Java Persistence API.
* [PostgreSQL](https://www.postgresql.org)
* [Swagger](https://swagger.io)
* [Docker](https://www.docker.com)


### Prerequisites
In order to be able to run the microservice, it is required to have the below technologies installed:
- [ ] Docker [[https://docs.docker.com/install](https://docs.docker.com/install)]
- [ ] Docker Compose [[https://docs.docker.com/compose/install](https://docs.docker.com/compose/install)]

### Installation
Once having Docker and Docker Compose installed correctly. Follow the steps listed below to run the application; including all its dependencies:
1. Verify Docker is up and running:
    ```docker --version```
    ```
    Docker version 19.03.5, build 633a0ea
    ```
2. Verify Docker Compose is installed: 
    ```docker-compose --version```
     ```
     docker-compose version 1.24.1, build 4667896b
     ```
3. Build and run the microservice with Compose:
    ```docker-compose --project-name=tourism-pass-mgmt up --detach```
    ```
   Building microservice
   Step 1/13 : FROM gradle:6.0.1-jdk8 AS build
   6.0.1-jdk8: Pulling from library/gradle
   7ddbc47eeb70: Pull complete
   c1bbdc448b72: Pull complete
   8c3b70e39044: Pull complete
   45d437916d57: Pull complete
   da4c04c54fa4: Pull complete
   2e619a1c4087: Pull complete
   1800cb84c672: Pull complete
   dcf6bc35d61f: Pull complete
   3e356ef9b249: Pull complete
   Digest: sha256:650329560eedb2bed81e02d5c1cb46ca91e6e02406dc899c58d868886a73b43e
   Status: Downloaded newer image for gradle:6.0.1-jdk8
    ---> 6543e2057a59
   Step 2/13 : COPY --chown=gradle:gradle . /home/gradle/src
    ---> 542eedf5b7f4
   Step 3/13 : WORKDIR /home/gradle/src
    ---> Running in 92934f5ba439
   Removing intermediate container 92934f5ba439
    ---> 28aa9aa3d618
   Step 4/13 : RUN gradle clean build bootJar --no-daemon
    ---> Running in 3bcd62a563d8
   
   Welcome to Gradle 6.0.1!
   
   Here are the highlights of this release:
    - Substantial improvements in dependency management, including
      - Publishing Gradle Module Metadata in addition to pom.xml
      - Advanced control of transitive versions
      - Support for optional features and dependencies
      - Rules to tweak published metadata
    - Support for Java 13
    - Faster incremental Java and Groovy compilation
    - New Zinc compiler for Scala
    - VS2019 support
    - Support for Gradle Enterprise plugin 3.0
   
   For more details see https://docs.gradle.org/6.0.1/release-notes.html
   
   To honour the JVM settings for this build a new JVM will be forked. Please consider using the daemon: https://docs.gradle.org/6.0.1/userguide/gradle_daemon.html.
   Daemon will be stopped at the end of the build stopping after processing
   > Task :clean UP-TO-DATE
   > Task :compileJava
   > Task :processResources
   > Task :classes
   > Task :bootJar
   > Task :jar SKIPPED
   > Task :assemble
   > Task :compileTestJava NO-SOURCE
   > Task :processTestResources NO-SOURCE
   > Task :testClasses UP-TO-DATE
   > Task :test NO-SOURCE
   > Task :check UP-TO-DATE
   > Task :build
   
   Deprecated Gradle features were used in this build, making it incompatible with Gradle 7.0.
   Use '--warning-mode all' to show the individual deprecation warnings.
   See https://docs.gradle.org/6.0.1/userguide/command_line_interface.html#sec:command_line_warnings
   
   BUILD SUCCESSFUL in 43s
   4 actionable tasks: 3 executed, 1 up-to-date
   Removing intermediate container 3bcd62a563d8
    ---> a1a2f0061085
   
   Step 5/13 : FROM openjdk:8-jre-slim
   8-jre-slim: Pulling from library/openjdk
   000eee12ec04: Pull complete
   2f1dc2bdcfe1: Pull complete
   c2a806caa98c: Pull complete
   89a5b0238e61: Pull complete
   Digest: sha256:171bf189bf031f412aabbbd6b531d47c0971822e31fe0faee3b38a45bead8b53
   Status: Downloaded newer image for openjdk:8-jre-slim
    ---> bf4f62306d0f
   Step 6/13 : EXPOSE 8080
    ---> Running in d077beb0b853
   Removing intermediate container d077beb0b853
    ---> fb970a1e5f1c
   Step 7/13 : RUN mkdir -p /opt/lpg/tourism_pass_management_system/jar
    ---> Running in ae51c0a62710
   Removing intermediate container ae51c0a62710
    ---> e5368db60b2a
   Step 8/13 : RUN mkdir -p /opt/lpg/tourism_pass_management_system/logs
    ---> Running in db68bffebad1
   Removing intermediate container db68bffebad1
    ---> e80679e4ed7f
   Step 9/13 : RUN mkdir -p /opt/lpg/tourism_pass_management_system/config
    ---> Running in 93c53e577e3b
   Removing intermediate container 93c53e577e3b
    ---> 6757c5a09215
   Step 10/13 : RUN chown -R $(whoami) /opt/lpg
    ---> Running in 0841040527c0
   Removing intermediate container 0841040527c0
    ---> 64120a48cc40
   Step 11/13 : COPY src/main/resources/config/log4j2.xml /opt/lpg/tourism_pass_management_system/config/log4j2.xml
    ---> cf5208df2822
   Step 12/13 : COPY --from=build /home/gradle/src/build/libs/*.jar /opt/lpg/tourism_pass_management_system/jar/tourism_pass_management_system.jar
    ---> 8a0f24bde7d5
   Step 13/13 : ENTRYPOINT ["java", "-jar", "/opt/lpg/tourism_pass_management_system/jar/tourism_pass_management_system.jar"]
    ---> Running in 491c4680a42f
   Removing intermediate container 491c4680a42f
    ---> ba2b85589a13
   
   Successfully built ba2b85589a13
   Successfully tagged tourism-pass-mgmt_microservice:latest
   WARNING: Image for service microservice was built because it did not already exist. To rebuild this image you must use `docker-compose build` or `docker-compose up --build`.
   Creating tourism-pass-mgmt_microservice_1 ... done
   Creating tourism-pass-mgmt_postgresql_1   ... done
   ```
   Command Options:
   * ```--project-name=tourism-pass-mgmt```: Specify an alternate project name (default: directory name). In this case _'tourism-pass-mgmt'_.
   * ```-detach```: Detached mode: Run containers in the background, print new container names.
 4. Verify the containers, volumes and network were created:
    * Containers: ```docker container ls```
        ```
         CONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS              PORTS                    NAMES
         b1d172abc2ae        sample_microservice              "java -jar /opt/lpg/…"   52 minutes ago      Up 52 minutes       0.0.0.0:8080->8080/tcp   tourism-pass-mgmt_microservice_1
         9c51e3236083        postgres                         "docker-entrypoint.s…"   52 minutes ago      Up 52 minutes       0.0.0.0:5432->5432/tcp   tourism-pass-mgmt_postgresql_1
        ```
    * Volumes: ```docker volume ls```
        ```
        DRIVER              VOLUME NAME
        local               sample_microservice-logs
        local               sample_postgres-data
        ```
    * Network: ```docker network ls```
        ```
        NETWORK ID          NAME                        DRIVER              SCOPE
        d5f8f306ed15        tourism-pass-mgmt_default   bridge              local
        ```
5. Verify the microservice can be accessible through Swagger UI:
    [http://localhost:8080/com/sample-system/swagger-ui.html](http://localhost:8080/com/sample-system/swagger-ui.html)
    
    ![Swagger: Sample System](misc/images/Swagger-TourismPassManagementSystem.jpg)
