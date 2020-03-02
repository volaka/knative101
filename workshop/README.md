# Introduction

In this lab, you'll learn about Knative, a new open source collaboration from IBM, Google, Pivotal, Red Hat, Cisco, and others. You'll create a new cluster on IBM Kubernetes Service \(IKS\), install Istio & Knative to that cluster, and then deploy a Node.js fibonacci application to Knative.

## What is Knative

[Knative](https://github.com/knative/docs) is an open source platform that was developed by IBM, Google, Pivotal, Red Hat, Cisco, and others. The goal is to extend the capabilities of Kubernetes to help you create modern, source-centric containerized, and serverless apps on top of your Kubernetes cluster. The platform is designed to address the needs of developers who today must decide what type of app they want to run in the cloud: 12-factor apps, containers, or functions. Each type of app requires an open source or proprietary solution that is tailored to these apps: Cloud Foundry for 12-factor apps, Kubernetes for containers, and OpenWhisk and others for functions. In the past, developers had to decide what approach they wanted to follow, which led to inflexibility and complexity when different types of apps had to be combined.

Knative uses a consistent approach across programming languages and frameworks to abstract the operational burden of building, deploying, and managing workloads in Kubernetes so that developers can focus on what matters most to them: the source code. You can use proven build processes that you are already familiar with, such as Kaniko, Dockerfile, Bazel, and others. By integrating with Istio, Knative ensures that your serverless and containerized workloads can be easily exposed on the internet, monitored, and controlled, and that your data is encrypted during transit.

### Knative Components

Knative comes with two key components, or _primitives_, that help you to deploy and manage your serverless apps in your Kubernetes cluster:

* **Serving:** The `Serving` primitive helps to deploy serverless apps as Knative services and to automatically scale them, even down to zero instances. To expose your serverless and containerized workloads, Knative uses Istio. When you install the managed Knative add-on, the managed Istio add-on is automatically installed as well. By using the traffic management and intelligent routing capabilities of Istio, you can control what traffic is routed to a specific version of your service, which makes it easy for a developer to test and roll out a new app version or do A-B testing.
* **Eventing:** With the `Eventing` primitive, you can create triggers or event streams that other services can subscribe to. For example, you might want to kick off a new build of your app every time code is pushed to your GitHub master repo. Or you want to run a serverless app only if the temperature drops below freezing point. For example, the `Eventing` primitive can be integrated into your CI/CD pipeline to automate the build and deployment of apps in case a specific event occurs.

We will also explore **Tekton Pipelines**, a project providing kubernetes-style resources for declaring CI/CD pipelines.

{% hint style="info" %}
The Knative open-source project deprecated the **Build** primitive in favor of the Tekton open-source project. The Build primitive provided you with tools to automate the build process for your app from source code to a container image. The Tekton project originated from the Knative project and provides advanced CI/CD features on top of the deprecated Knative Build primitive. For more information, see the [Tekton open-source project](https://tekton.dev).
{% endhint %}

### Knative Personas

Two of the key Knative personas are **Developers** and **platform providers**. 

* Knative components offer developers Kubernetes-native APIs for deploying serverless-style functions, applications, and containers to an auto-scaling runtime. 
* Knative components are intended to be integrated into more polished products that cloud service providers or in-house teams in large enterprises can then operate.

  Any enterprise or cloud provider can adopt Knative components into their own systems and pass the benefits along to their customers.

![knative personas](.gitbook/assets/audience.png)

## What will we do?

The Knative application you'll create is a **fibonacci sequence app**. When provided with the number _n_, it will return the first n numbers of the fibonacci sequence: 1, 1, 2, 3.... 

You'll also deploy a _vnext_ of the application, which starts the fibonacci sequence with 0 instead of 1: 0, 1, 1, 2, 3.... The application will be given a domain, which you'll be able to curl to get the fibonacci results.

### IBM Cloud Kubernetes Service - Knative Add-On

Managed Knative on IBM Cloud Kubernetes Service is a [managed add-on](https://cloud.ibm.com/docs/containers?topic=containers-managed-addons#managed-addons) that integrates Knative and Istio directly with your Kubernetes cluster. The Knative and Istio versions in the add-on are tested by IBM and supported for the use in IBM Cloud Kubernetes Service. For more information about managed add-ons, see [Adding services by using managed add-ons](https://cloud.ibm.com/docs/containers?topic=containers-managed-addons#managed-addons).

**Are there any limitations?**

* The managed Knative add-on version 0.12.1 requires and installs Istio 1.4 with the add-on. You cannot use the Knative add-on with Istio 1.3. Before you install Knative, you can check your Istio version by running `ibmcloud ks cluster addons -c <cluster_name_or_ID>`. If you have Istio 1.3 and want to use the managed Knative add-on, you must [uninstall Istio 1.3](https://cloud.ibm.com/docs/containers?topic=containers-istio#istio_uninstall).
* The Knative add-on can be enabled in clusters that run Kubernetes version 1.16 or later only.

## What will we learn?

You'll learn to:

* deploy applications using kubectl with a configuration yaml file, 
* deploy applications using the kn CLI tool,
* be able to see your application scale up when in use,  
* scale back down to zero pods when it's not being used,
* work with revisions and routes, sending some percentage of your traffic to a new revision.

![diagram of the app created in this lab](.gitbook/assets/knativeappdiagram.png)

Get started with the [workshop](exercise-0.md).

