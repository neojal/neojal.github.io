# Kubernetes for Java Developers

## Preconditions

* There is a Rest Spring Boot project: restful-web-services.

## Building a Docker Image from Java project 

* Creating a maven repository with all the dependencies of *restful-web-services* 
project, then package the repository directory:

```commandline
[neojal@manjaro restful-web-services]$ mvn -Dmaven.repo.local=./repository clean package

$ tar -cf repository.tar.gz ./repository
```

```commandline
```


```commandline
```


```commandline
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


