# Create IBM Cloud Account and Install Developer Tools

If you already have an IBM Cloud account with the following tools installed, you can skip these steps:

* `ibmcloud` CLI for interacting with IBM Cloud
* `ibmcloud ks` plugin for IBM Kubernetes Service
* `ibmcloud cr` plugin for IBM Container Registry
* `kubectl` CLI for interacting with Kubernetes
* `kn` CLI for interacting with Knative

## Create an IBM Cloud Account

1. Create an account on [IBM Cloud](https://cloud.ibm.com/registration).

## Installing the IBM Cloud developer tools and plugins

Detailed information can be found in [IBM Cloud Kubernetes Service documentation](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install#cs_cli_install_steps).

{% hint style="info" %}
If you want to use the IBM Cloud console instead, you can run CLI commands directly from your web browser in the [IBM Cloud Shell](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install#cloud-shell) or, after your cluster is created, the [Kubernetes Web Terminal](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install#cli_web).

In this workshop, we are going to use this option, that's why you can skip this step.
{% endhint %}

1. Download and install the `ibmcloud` [command line tool.](https://cloud.ibm.com/docs/cli/index.html#overview)
2. Install the `ks` \(kubernetes-service\) plugin:

   ```text
   ibmcloud plugin install kubernetes-service
   ```

3. Install the `cr` \(container-registry\) plugin:

   ```text
   ibmcloud plugin install container-registry
   ```

4. Authorize `ibmcloud`:

   ```text
   ibmcloud login
   ```

## Install Kubectl

The Kubernetes command-line tool, kubectl, can be used to deploy and manage applications on Kubernetes. Using kubectl, you can inspect cluster resources; create, delete, and update components; look at your new cluster; and bring up example apps.

1. Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl)

## Install kn CLI

The Knative command-line tool, kn provides a set of commands to interact with a Knative installation. Let's install kn as well.

1. Install the kn client by following their [instructions for installation](https://github.com/knative/client/blob/master/docs/README.md#installing-kn). You should be able to download the latest binary executable, and add it to your path, and ensure the file is executable. To ensure the file is executable, run the following command:

   ```text
    chmod +x kn
   ```

Continue on to [exercise 1](exercise-1.md).

