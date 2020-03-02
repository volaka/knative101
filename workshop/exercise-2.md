# Install Istio and Knative on Your Cluster

Knative is currently built on top of both Kubernetes and Istio. If you want to learn more about Kubernetes or Istio, you can check out the labs [Kube101](https://github.com/IBM/kube101/tree/master/workshop) and [Istio101](https://github.com/IBM/istio101/tree/master/workshop). When you install Knative on IKS, it will install Istio for you automatically.

## Install Knative

1. To install Knative, first make sure you have the latest Kubernetes plugin:

   ```text
    ibmcloud plugin update
   ```

2. Next ask for Knative to be installed:

   ```text
    ibmcloud ks cluster-addon-enable knative --cluster $MYCLUSTER
   ```

   You will be prompted to install Istio - when you see this prompt, enter `y`.

3. The install process may take a minute or two. To know when it's done you can run two commands - first see if the Istio and Knative namespaces are there:

   ```text
   kubectl get namespace
   ```

   and you should see something like:

   ```text
   NAME                 STATUS   AGE
   default              Active   7d18h
   ibm-cert-store       Active   7d18h
   ibm-system           Active   7d18h
   istio-system         Active   7d17h
   knative-build        Active   7d17h
   knative-eventing     Active   7d17h
   knative-monitoring   Active   7d17h
   knative-serving      Active   7d17h
   knative-sources      Active   7d17h
   kube-public          Active   7d18h
   kube-system          Active   7d18h
   ```

   Notice the `istio-system` namespace, and the `knative-...` namespaces.

   Once the namespaces are there, check to see if all of the Istio and Knative pods are running correctly:

   ```text
   kubectl get pods --namespace istio-system
   kubectl get pods --namespace knative-serving
   kubectl get pods --namespace knative-build
   ```

   You could check the pods in all of the Knative namespaces, but for this workshop only "serving" and "build" are required.

Example Ouput:

```text
   NAME                          READY   STATUS    RESTARTS   AGE
   activator-df78cb6f9-jpvs7     2/2     Running   0          38s
   activator-df78cb6f9-nhzhf     2/2     Running   0          37s
   activator-df78cb6f9-qjg8w     2/2     Running   0          37s
   autoscaler-6fccb66768-m4f2q   2/2     Running   0          37s
   controller-56cf5965f5-8pwcg   1/1     Running   0          35s
   webhook-5dcbf967cd-lxzmk      1/1     Running   0          35s
```

If all of the pods shown are in a `Running` or `Completed` state then you should be all set.

Continue on to [exercise 3](exercise-3.md).

