# Learning Docker

## Introduction

Docker mission: Build, Ship & Run distributed applications.  

* Build: Docker Image.
* Ship: Docker Hub (or another repository)
* Run: Docker Container.

Avoid single point of failure by running multiple containers.  


### What is a Container (General)?

A collection of software processes unified by one namespace,
with access to an operating system kernel that shares with other
containers and little to no access between containers.

### Docker Instance

A runtime of a Docker image contains three things:

1. A Docker image.
2. An Execution environment.
3. A standard set of instructions

### Docker Engine

Comprised of the runtime and packaging tool; **must** be installed in
the hosts that run Docker.

### Difference between VM and a Container:

#### VM:

- The entire guest operating system to interact with the apps.
    
#### Container:

- Shares the host kernel with other containers.
- Needs Docker Engine installed on the Host.
- Run as isolated processes on the host OS.
- Includes the application and all of its dependencies.
       
### Container benefits for Developers:

Apps are:  

* portable
* packaged in a standard way

Deployment is:

* Easy
* Repeatable
* Automated testing, packaging, and integrations
* Support new microservice architectures
* Alleviate platform compatibility issues

### Benefits for DevOps:

* Reliable deployments: improve speed and frequency of releases.
* Consistent application lifecycle: configure once and run multiple times.
* Improves communication between developers and devops.

# Learning Kubernetes
Container orchestrator: manages containers in a host or across your whole infrastructure.

## K8S introduction

**Container orchestrator features**:  
 
* Provision hosts
* Instantiate containers on a host
* Restart failing containers
* Expose containers as service outside the cluster
* Scale the cluster up and down

Kubernetes is a platform to schedule and run containers on:

- clusters of VM
- bare metal
- private data center
- public cloud

## Kubernetes Features

**Multi-Host Container Scheduling**:

- Done by the _kube-scheduler_
- Assigns pods to nodes at runtime
- Checks resources, quality of service and user specifications before scheduling
    
**Availability**:

- Kubernetes _master node_ can be deployed in a highly available configuration
- Multi region deployments available

**Scalability**:

- Registration: seamless working nodes register themselves with master node.
- Service discovery: automatic detection of services and endpoints via DNS or environment variables

**Persistent Storage**

* Useful and important feature when working with containers
* Pods can use persistent volumes to store data
* Data retained across pod restarts and crashes

**Logging and Monitoring**:

* Application monitoring built in
    * TCP, HTTP, or container execution health check
* Node health check
    * Failures monitored by node controller
* Kubernetes status
    * can also be monitored via add-ons
    
**Secrets management**:

* Sensitive data is first-class citizen
* Mounted as data volumes or environment variables
* Specific to namespace

## Kubernetes Cluster Architecture

![k8s-architecture](/assets/k8s-architecture.png | width=500 )

[Components](https://kubernetes.io/docs/concepts/overview/components/)

* Master node:
 - API server
 - Scheduler
 - Controlller Manager
 
* etcd
 - configuration/schedules storage
  
* kubectl
 - kubeconfig
  
* Work node
 - kubelet
 - kube proxy
 - docker
  - pod
   - container(s)
 
## Nodes and Pods 

### Nodes

A node is a worker machine in K8s, previously known as minion. 
A node may be a VM or physical machine, depending on the cluster. 

* Node Requirements:
    - a Kubelet running
    - container tooling like Docker
    - a kube-proxy process running
    - supervisord

In prod, it's recommended to have at least a 3 node cluster.    

### Pod

Pods are the smallest deployable units of computing that can be created 
and managed in Kubernetes.

A pod is a group of one or more containers with shared storage/network 
and a specification for how to run the containers. 

The containers in a pod share the same IP address and port space, 
and can communicate between them with localhost.

Containers in a pod share a context.

* Pod lifecycle:
    - Pending
    - Running
    - Succeeded
    - Failed
    - CrashLoopBackOff
