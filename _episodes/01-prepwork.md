---
title: "Prep-work: Kubernetes Clusters"
teaching: 0
exercises: 0
questions:
- "What is Kubernetes?"
- "What is a Kubernetes cluster and why do I need one?"
objectives:
- "Learn the very basics of Kubernetes"
- "Learn a bit about the architecture of a Kubernetes cluster"
keypoints:
- "Kubernetes is an orchestrator of containers.  It is most useful when it is run in a cluster of computers"
- "Commercial K8s clusters are a good option for large computing needs."
- "We can run our containerized CMSSW jobs and subsequent analysis workflows in a K8s cluster."
---

## Introduction

Most of you have been working with Docker containers throughout this workshop.  As you know now, one could see these Docker containers like isolated machines that can run on a host machine in a very efficient way.  Your desktop or laptop could actually run several of these containers if enough resources are available.  For instance, you could think that one can maximize the hardware resources by running multiple CMSSW open data containers in one desktop.  Imagine, if you could run 10 CMSSW containers (each over a single root file) at the same time in a single physical machine, then it will take you 10 times less time to skim a full dataset.  

Now, if you had more machines available, let's say 3 or 4, and in each one of them you could run 10 containers, that will certainly speed up the data processing (specially the first stage in our analysis flow example, remember.)  Now, if you could have access to many more machines, then a few problems may appear.  For instance, how would you install the software required in all those machines? Would there be enough personpower to take care of that?  How would you take care of, and babysit all those containers?  

The answer to most of these questions is Kubernetes, and, particularly, Kubernetes running on commercial clusters.  Kubernetes (K8s) software is said to be an orchestrator of containers.  Not necessarily Docker containers, but any brand which shares the same basic technological principles.

In this lesson you will learn about using commercial cloud computing resources in order to process CMS open data.  Basically, we will introduce you to the arts of using a few machines (a cluster of computers) to run your containerized open data analysis workflows and manage them with tools that interact with the Kubernetes software.  

## K8s architecture

We believe that learning a bit a bout K8s architecture will help you understand better what goes on in the next episodes of this lesson.  In simple terms, when you access a cloud K8s cluster you are getting access to a cluster of computers run by Kubernetes .  These computers will have main servers (also called control planes) and some worker nodes.  The main servers will take care of the bookkeeping and handling of the worker nodes, while the worker nodes will be the ones running your containers (spoiler alert, each container is essentially called a *pod* in the K8s abstraction).

Take into account that K8s commercial clusters were built with software and application developers in mind.  They are mostly used to run services like web pages with database access, apps, etc., but the technology works well for our needs, i.e., sending batch jobs and getting some output.

Plese watch this video, which will explain the basic Kubernetes cluster architecture with a nice analogy:

<iframe width="560" height="315" src="https://www.youtube.com/embed/8C_SCDbUJTg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





{% include links.md %}
