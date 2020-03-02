# Introduction

In this lab, you'll learn about Knative, a new open source collaboration from IBM, Google, Pivotal, Red Hat, Cisco, and others. You'll create a new cluster on IBM Kubernetes Service \(IKS\), install Istio & Knative to that cluster, and then deploy a Node.js fibonacci application to Knative.

## What is Knative

Knative is built on top of Istio & Kubernetes, and is a set of primitives for enabling serverless applications on Kubernetes. 

### Knative Components

Knative consists of the **Serving** and **Eventing** components.

* Serving supports **serving your applications, managing traffic, as well as routing and autoscaling**. 
* Eventing enables you to create **event producers and consumers** for your application.

We will also explore **Tekton Pipelines**, a project providing kubernetes-style resources for declaring CI/CD pipelines.

### Knative Personas

Two of the key Knative personas are **Developers** and **platform providers**. 

* Developers can use Knative directly \(or through an API\) to build Serverless applications on top of Kubernetes. 
* Platform providers can use the Knative primitives to build their own Serverless platform on Kubernetes.

![knative personas](.gitbook/assets/audience.png)

## What will we do?

The Knative application you'll create is a **fibonacci sequence app**. When provided with the number _n_, it will return the first n numbers of the fibonacci sequence: 1, 1, 2, 3.... 

You'll also deploy a _vnext_ of the application, which starts the fibonacci sequence with 0 instead of 1: 0, 1, 1, 2, 3.... The application will be given a domain, which you'll be able to curl to get the fibonacci results.

## What will we learn?

You'll learn to:

* deploy applications using kubectl with a configuration yaml file, 
* deploy applications using the kn CLI tool,
* be able to see your application scale up when in use,  
* scale back down to zero pods when it's not being used,
* work with revisions and routes, sending some percentage of your traffic to a new revision.

![diagram of the app created in this lab](.gitbook/assets/knativeappdiagram.png)

Get started with the [workshop](exercise-0.md).

