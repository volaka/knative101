# Introduction

## Knative 101

In this lab, you'll learn about Knative, a new open source collaboration from IBM, Google, Pivotal, Red Hat, Cisco, and others. You'll create a new cluster on IBM Kubernetes Service \(IKS\), install Istio & Knative to that cluster, and then deploy a Node.js fibonacci application to Knative.

* Create IBM Cloud Account
* Create/Claim IBM Kubernetes Service \(IKS\)
* Install Istio & Knative on IKS
* Deploy a Node.JS fibonacci application to Knative using various methods
* **Have fun!**

### About this workshop <a id="about-this-workshop"></a>

The introductory page of the workshop is broken down into the following sections:

* ​[Agenda](https://ibm-developer.gitbook.io/workshop-template/#agenda)​
* ​[Compatibility](https://ibm-developer.gitbook.io/workshop-template/#compatibility)​
* ​[Technology Used](https://ibm-developer.gitbook.io/workshop-template/#technology-used)​
* ​[Credits](https://ibm-developer.gitbook.io/workshop-template/#credits)​

## Agenda <a id="agenda"></a>

| ​Name | Description |
| :--- | :--- |
| [Pre-work 0.1: Registration and Required Tools](prework/exercise-0.md) | IBM Cloud Account registration and intallation of required tools for the workshop |
| [Pre-work 0.2: IBM Cloud Kubernetes Service​](prework/exercise-1.md) | IBM Cloud Kubernetes Service creation. |
| [Pre-work 0.3: Install Istio and Knative](prework/exercise-2.md) | Installation of Istio and Knative on IKS |
| [Concepts 1.1: Knative](knative.md) | What is Knative |
| [Concepts 1.2: Knative Serving Component](knative-serving-component.md) | Explaining Knative Serving component. |
| [Workshop 2.1: Deploy First Application to Knative](exercise-3.md) | Explaining workshop |
| [Workshop 2.2: Deploy using Knative Client](deploy-using-knative-client.md) | Deplyoment using Knative client tool `kn` |
| [Workshop 2.3: Deploy using YAML and Kubectl](deploy-using-yaml-and-kubectl.md) | Deployment using yaml and Kubernetes client tool `kubectl` |
| [Workshop 2.4: Deploy vnext version and Apply Traffic Shifting](exercise-5.md) | Deployment of v2 of the application |

## Compatibility <a id="compatibility"></a>

This workshop has been tested on the following platforms:

* **osName**: MacOS Catalina 10.15, Linux \(IBM Cloud Shell\)

## Technology Use <a id="technology-used"></a>

### [Kubernetes](https://kubernetes.io/)

Kubernetes \(K8s\) is an open-source system for automating deployment, scaling, and management of containerized applications.

In this workshop, we will use [IBM Cloud Kubernetes Service.](https://www.ibm.com/cloud/container-service/)

### [Knative](https://github.com/knative/docs)

Knative is an open source platform that was developed by IBM, Google, Pivotal, Red Hat, Cisco, and others. The goal is to extend the capabilities of Kubernetes to help you create modern, source-centric containerized, and serverless apps on top of your Kubernetes cluster

### [Istio](https://istio.io)

Cloud platforms provide a wealth of benefits for the organizations that use them. However, there’s no denying that adopting the cloud can put strains on DevOps teams. Developers must use microservices to architect for portability, meanwhile operators are managing extremely large hybrid and multi-cloud deployments. Istio lets you connect, secure, control, and observe services.

At a high level, Istio helps reduce the complexity of these deployments, and eases the strain on your development teams. It is a completely open source service mesh that layers transparently onto existing distributed applications. It is also a platform, including APIs that let it integrate into any logging platform, or telemetry or policy system. Istio’s diverse feature set lets you successfully, and efficiently, run a distributed microservice architecture, and provides a uniform way to secure, connect, and monitor microservices.

## Credits <a id="credits"></a>

* [https://github.com/IBM/knative101](https://github.com/IBM/knative101)

