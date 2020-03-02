# Create a Cluster on IBM Cloud

If you have already created a cluster on IBM Cloud and have set the context for kubectl you can skip these steps.

## Create a standard cluster

This lab requires a standard \(paid\) cluster. Create a new standard cluster from the [IBM Cloud UI](https://cloud.ibm.com/containers-kubernetes/catalog/cluster/create).

1. To ensure the cluster is large enough to host all the Knative and Istio components, the recommended configuration for a cluster is:
   * Kubernetes version 1.11 or later
   * 4 vCPU nodes with 16GB memory \(`b2c.4x16`\)
2. It is required to select the worker zone, as well as to create a unique cluster name for your cluster. Ensure you've selected Kubernetes version 1.11.x, which may not be the default.
3. Click `Create Cluster`.
4. Export the cluster name you chose as an environment variable for use in the lab.

   ```text
    export MYCLUSTER=<your_cluster_name>
   ```

5. Wait while your cluster is fully deployed. Repeat this command until the state of the cluster is `normal`.

   ```text
    ibmcloud ks clusters | grep $MYCLUSTER
   ```

## Set context for kubectl

Set the context for your cluster in your CLI. Every time you log in to the CLI to work with the cluster, you must run this command to set a path to the cluster's configuration file as a session variable. The Kubernetes CLI uses this variable to find a local configuration file and certificates that are necessary to connect with the cluster in IBM Cloud.

1. Download the configuration file and certificates for your cluster using the `cluster-config` command.

   ```text
    ibmcloud ks cluster-config $MYCLUSTER
   ```

2. Copy and paste the output command from the previous step to set the `KUBECONFIG` environment variable and configure your CLI to run `kubectl` commands against your cluster.

   Example:

   ```text
    export KUBECONFIG=/Users...
   ```

3. Validate access to your cluster by viewing the nodes in the cluster.

   ```text
    kubectl get node
   ```

Continue on to [exercise 2](exercise-2.md).

