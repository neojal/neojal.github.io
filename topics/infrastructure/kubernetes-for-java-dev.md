# Kubernetes for Java Developers

https://github.com/arun-gupta/lil-kubernetes-for-java
https://github.com/GoogleContainerTools/jib
https://www.aquasec.com/wiki/display/containers/Docker+Architecture

## K8s workflow for Java developers

1. Package Java Application
2. Create and Publish Docker Image
3. Create a Kubernetes Resource Manifest
4. Create K8s cluster
5. Deploy Kubernetes resources

## Docker Workflow

* Registry: is a stateless server-side which stores docker images.
* Client Host: Docker CLI (dev localhost or CI/CD pipeline) to interact with Docker Daemon.
    - docker container run
    - docker image push
    - docker image pull
* Server Host: images are downloaded here and containers run
    - Docker Engine Rest API: API used by applications to interact with the Docker Daemon.
    - Docker Daemon: persistent background process that manages Docker images, containers, networks and volumes.

* Client Host gives the command to Server Host, which then communicates with Registry on client's behalf.

## Create Docker Images

* Create from Dockerfile (always starts with FROM). Multiple FROM statements are allowed, enables run stages.

* Build image from Dockerfile, then basic run, and then run with some options:

```shell
$ docker image build

$ docker container run <image name>

$ docker container run <-d detached or background> <-it interactive> -p <port:port> <image name>
```

* You can use **.dockerignore** file to filter files to be added while building the image.

* Multi-stage Dockerfile.
    * Build stage (FROM maven): builds the Application using a Maven container.
    * Production stage (FROM openjdk): in production only jdk is required, not maven or anything else.
    
    
```Dockerfile
FROM maven:3.5-jdk-8 as BUILD

ADD repository.tar.gz /usr/share/maven/ref/

COPY . /usr/src/app
WORKDIR /usr/src/app
RUN mvn -s /usr/share/maven/ref/settings-docker.xml package

FROM openjdk:8-jre
EXPOSE 8080 5005
COPY --from=BUILD /usr/src/app/target /opt/target
WORKDIR /opt/target
ENV _JAVA_OPTIONS '-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005'

CMD ["java", "-jar", "greeting.war"]
```
* See chapter 2 for Docker commands:
https://github.com/arun-gupta/lil-kubernetes-for-java/tree/master/chapter2

## Build a Docker Image Using JIB

Jib builds optimized Docker and OCI images for your Java applications without a Docker daemon 
- and without deep mastery of Docker best-practices. 
It is available as plugins for Maven and Gradle and as a Java library.

https://github.com/GoogleContainerTools/jib

* Builds Docker images for Java apps.
* Docker daemon not needed.
* No Dockerfile required.

* In application's pom.xml, there is a jib profile

```shell
[neojal@manjaro app]$ mvn package -Pjib
```

## Minimal Docker image using custom JRE

* Tools to create custom/minimal JRE:
    - jlink
    - jdeps




## Preconditions

* There is a Rest Spring Boot project: restful-web-services.

## Building a Docker Image from Java project 

* Creating a maven repository with all the dependencies of *restful-web-services* 
project, then package the repository directory:

```shell
[neojal@manjaro restful-web-services]$ mvn -Dmaven.repo.local=./repository clean package

$ tar -cf repository.tar.gz ./repository
```

```shell
```


```shell
```


```shell
```


```commandline
```

    
## Kubernetes concepts

https://kubernetes.io/docs/concepts/





* Kubelet

Primary node agent that runs on each node. The kubelet works in terms of a 
PodSpec. A PodSpec is a YAML or JSON object that describes a pod.

* CNCF

Cloud Native Computing Foundation


