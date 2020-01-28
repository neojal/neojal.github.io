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
       
### Containers benefits for Developers:

Apps are:  

* portable:
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

## K8S introduction

Definition: An open-source platform designed to automate deploying, scaling, 
and operating application containers.

Goal: to foster an ecosystem of components and tools that relieve the 
burden of running applications in public and private clouds.

Kubernetes is a platform to schedule and run containers on:

- clusters of VM
- bare metal
- private data center
- public cloud

### Container orchestration

- Provision hosts
- Instantiate containers on a host
- Restart failing containers
- Expose containers as services outside the cluster
- Scale the cluster up and down

## Kubernetes Features

* Multi-Host Container Scheduling

    - Done by the kube-scheduler.
    - Assigns pods ton nodes at runtime
    - Checks resources, quality of service
    
* Scalability and Availability
    
    - Multi region deployments available.

* Persistent Storage

## Kubernetes Cluster Architecture

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
