---
title: "Demo: Creating a cluster"
teaching: 20
exercises: 0
questions:
- "What are the basic concepts and jargon I need to know?"
- "Do do I manually create a K8s cluster on the GCP"
objectives:
- "Learn a few words and concepts that will be used during this lesson"
- "Lear how to create a K8s cluster from scratch"
keypoints:
- "It takes just a few clicks to create you own K8s cluster"
---

## Introduction

In this demonstration we will show you the very basic way in which you can create a computer cluster (a Kubernetes cluster to be exact) in the cloud so you can do some data processing and analysis using those resources.  In the process we will make sure you learn about the jargon.  During the hands-on session tomorrow, a cluster similar to this one will be provided to you for the exercises.  

## Basic concepts

### The Google Cloud Platform (GCP)

A place on the web that interfaces the user with all the different services that google provide on the *cloud*.

![](https://www.seekpng.com/png/full/357-3579104_what-is-google-cloud-platform-google-cloud-platform.png)

{% include links.md %}

### GCP Console

The exact name of the GCP interface where you can explore all the different services that GCP provides.  They include, but are not limited to individual virtual machines, disk storage, kubernetes clusters, etc.

![](https://cloudmaven.github.io/cloud101_cloudproviders/fig/03-gcp-intro-0001.png)

### Google Kubernetes Engine

A Google service to create Kubernetes clusters and run conteinerized application and/or jobs/workflows.

### Kubernetes (K8s)

Software which orchestrates containers in a computer cluster.  You already had a chance to learn about its architecture.

![](https://1.bp.blogspot.com/-kCijQkEkmA8/X9ctU83lcJI/AAAAAAAAF5U/GayBI9yQ-PsUuGI9L4Mf8dJwsByp6g8WQCLcBGAsYHQ/s1192/k8%2Barchitecture.PNG)


### Workflow

A series of sequential operations in order to achieve a final result.  In our case it could be, for instance

`skimming` -> `merging output files` -> `EventLoop analysis of resulting files` -> `Plottin histograms`

In the context of the cloud, they are written in `yaml` files.

### Pod

The smallest abstraction layer in a K8s cluter.  For any practical purposes, a pod is an abstraction of a container running in the K8s cluster.

![](https://res.cloudinary.com/escalante-rep/image/upload/v1589159144/i14yfj2jn5nm70bzekxu.jpg)

### Deployment

This is an abstraction layer which is above *pods*.  In practice, you always create deployments in K8s, not pods.

### Argo

Argo Workflows is an open source container-native workflow engine for orchestrating parallel jobs on Kubernetes.

![](https://argoproj.github.io/argo-workflows/assets/argo.png)


## Creating your own cluster on GKE

For the hands-on part of this lesson you will not have to create the cluster for yourself, it will be already done for you.  For pedagogical reasons, however, we will show an example of how to do it by hand.  The settings below should be good and cheap enough for CMSSW-related workflows.

* Get to the Console
* Create a new project or select one of your interest (if you already have one)
![](../fig/project.png)
* Click on the Kubernetes engine/clusters section on the left side menu
![](../fig/k8sengine.png)
* Select create cluster (standard)
![](../fig/createstandard.png)
* Give it a name
![](../fig/clustername.png)
* Many ways to configure the cluster, but let's try an efficient one with autoscaling
* Go to default pool
* Choose size: 1 node
* Autoscaling 0 to 4
  ![](../fig/defaultpool.png)
* Go to Nodes
* Choose a machine e2-standar-4
* Leave the rest as it is
* Hit create
![](../fig/create.png)
* Creation will take while

While we wait, lets inspect the Cloud shell...

## Cloud shell

GCP provides an *access machine* so you can interact with their different services, including our newly created K8s cluster.  This machine (and the terminal) is not really part of the cluster. As was said, it is an entry point.  From here you could *connect* to your cluster.

![](https://cloud.google.com/shell/docs/images/cloud-shell-gcloud.gif)

* Get verified for login, type:
```
gcloud auth login
```
Then follow the proceure for the verification.
![](../fig/auth.png)

This is something you will have to do only once.  For the hands-on part of the lesson, it is likely that you were already authenticated.

## The `gcloud` command

The gcloud command-line interface is the primary CLI tool to create and manage Google Cloud resources. You can use this tool to perform many common platform tasks either from the command line or in scripts and other automations.

## Connect to your cluster

Once the cluster is ready (green check-mark should appear)

* Click on the connect button of your cluster:
![](../fig/connect.png)

* Execute that command in the cloud shell:
![](../fig/accesscluster.png)
