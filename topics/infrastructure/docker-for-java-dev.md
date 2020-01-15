# A Start to Finish Guide to Docker with Java
https://stackify.com/guide-docker-java/

# Docker for Java developers

https://github.com/arun-gupta/docker-for-java

## Running your first container

```shell script
# start docker daemon 
$ sudo dockerd  

# login to registry, so images can be downloaded
$ docker login

# run container interactively (downloads it from registry if not present)
$ docker container run -it jboss/wildfly

# run container in background
$ docker container run -d jboss/wildfly

# list active containers
$ docker container ls

# list all containers
$ docker container ls -a

# stop container by id or name
$ docker container stop 

# run container setting a name
$ docker container run --name wildfly -d jboss/wildfly

# removes a container even if running
$ docker container rm -f wildfly

# starts container and executes a single command instead of wildfly server.
$ docker container run --name wildfly -it jboss/wildfly bash

# now we are inside the container.
[jboss@d20566e5550b ~]$ pwd
/opt/jboss

# exit and finish container.
[jboss@d20566e5550b ~]$ exit
$
```

## Ports

```shell script
# -P runs the container and redirects traffic to a random port
$ docker container run --name wildfly -P -d jboss/wildfly

# see the port
$ docker container ls

ONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                     NAMES
9adb133f5324        jboss/wildfly       "/opt/jboss/wildfly/…"   About a minute ago   Up About a minute   0.0.0.0:32769->8080/tcp   wildfly

# see wildfly container logs
$ docker container logs wildfly
```
Open in web browser: http://localhost:32769/

 
```shell script
# -p 8080:8080 we specify the redirection ports
$  docker container run --name wildfly -p 8080:8080 -d jboss/wildfly
```
Open in web browser: http://localhost:32769/

## Volume Mapping 

Mapping/mounting a local directory into a container.

```shell script
# remove the existent wildfly container.

# volume mapping with -v option
$ docker container run -d --name web -p 8080:8080 -v `pwd`/webapp.war:/opt/jboss/wildfly/standalone/deployments/webapp.war jboss/wildfly
 ```

Now the webapp is running in the container:
http://localhost:8080/webapp/resources/persons

## Create your first Docker Image (Dockerfile)

Create an empty directory, then create a Dockerfile.

```shell script
$ vim Dockerfile
```

```dockerfile
FROM ubuntu
 
CMD echo "Hello world!"
```

```shell script
$ docker image --help

# build the image, tag helloworld, . this context
$ docker image build -t helloworld .

# history
$ docker history helloworld

# run helloworld container
$ docker container run helloworld

```

If the directory ins't empty, then its contents will be sent to the container. 

## Create your first Java Docker Image (Dockerfile)

Explore DockerHub: https://hub.docker.com/_/openjdk

In a new directory, then create a Dockerfile:

```dockerfile
FROM openjdk
CMD java -version
```

Then build (setting a tag name) and run the image:

```shell script
$ docker image build -t hellojava .

$ docker image ls

$ docker container run hellojava
penjdk version "13.0.1" 2019-10-15
OpenJDK Runtime Environment (build 13.0.1+9)
OpenJDK 64-Bit Server VM (build 13.0.1+9, mixed mode, sharing)

```

Using alpine image which is smaller:

```dockerfile
FROM openjdk:jdk-alpine
CMD java -version
```

```shell script
$ docker image build -t hello-jdk-alpine .

$ docker image ls

$ docker container run hello-jdk-alpine
openjdk version "1.8.0_171"
OpenJDK Runtime Environment (IcedTea 3.8.0) (Alpine 8.171.11-r0)
OpenJDK 64-Bit Server VM (build 25.171-b11, mixed mode)

```

## Docker Machine

We're using: https://hub.docker.com/r/jboss/wildfly, here is a description of how to run this image.

Some new Dockerfile commands:

* COPY: copy new files or directories to container filesystem.
* ADD: copies then allows file auto-extraction in the image:
    * ADD app.tar.gz /opt/var/myapp
    * Can download files from URL, but recommended curl of wget.
    
```dockerfile
FROM jboss/wildfly

COPY ../webapp.war /opt/jboss/wildfly/standalone/deployments/webapp.war
```

```shell script
$ docker run -p 8080:8080 -d helloweb
```

Then go to: http://localhost:8080/webapp/resources/persons
    
## Docker and Maven

