# Set up a Private Container Image Registry and Obtain Credentials

In the previous exercises, we deployed a container to Knative directly from dockerhub. What if we want to build our own container from source? In this lab, we'll use the [IBM Container Registry](https://console.bluemix.net/docs/services/Registry/registry_overview.html#registry_overview) to host our container images since you already have access to this through your IBM Cloud Account. IBM Container Registry enables you to store and distribute container images in a fully managed private registry.

1. You will need to first create an IBM Container Registry namespace. Let's confirm you're logged in.

   ```text
    ibmcloud login
   ```

   When prompted, select your own account, and then enter the number for the region `us-south`.

2. Add a namespace to your account. You must create at least one namespace to store images in IBM Cloud Container Registry. Choose a unique name for your first namespace. A namespace is a collection of related repositories \(which in turn are made up of individual images\). You can create multiple namespaces as well as control access to your namespaces by using IAM policies.

   ```text
    ibmcloud cr namespace-add <my_namespace>
   ```

3. Create an API key. This API key can be used to automate pushing and pulling of Docker images to and from your namespaces. The automated build processes you'll be setting up will use this key to access your images.

   ```text
    ibmcloud iam api-key-create mykey -d "API key for IBM Cloud"
   ```

4. The CLI output should include the API Key value. Create an environment variable containing your key.

   ```text
    export MYAPIKEY=<your_api_key_value>
   ```

## Provide Container Registry Credentials to Cluster

This lab will need credentials for authenticating to your private container registry. First, we'll need to create a `Secret` to store the credentials for this registry. This secret will be used for the knative-serving component to pull down an image from the container registry.

A `Secret` is a Kubernetes object containing sensitive data such as a password, a token, or a key. You can also read more about [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/).

1. Let's create a secret, which will be a `docker-registry` type secret. This type of secret is used to authenticate with a container registry to pull down a private image. We can create this via the commandline. For username, simply use the string `iamapikey`. For `<api_key_value>`, use the api key you made note of earlier.

   ```text
    kubectl --namespace default create secret docker-registry ibm-cr-secret  --docker-server=us.icr.io --docker-username=iamapikey --docker-password=$MYAPIKEY
   ```

2. We will also need a secret for the build process to have credentials to push the built image to the container registry. To create this secret, we'll first need to base64 encode our username and password for IBM Container Registry. For username, you will use the string `iamapikey`. The base64 encoding of `iamapikey` should be: `aWFtYXBpa2V5` - which is already in the yaml file. Let's base64 encode our apikey, and copy it.

   ```text
    echo -n $MYAPIKEY | base64 -w0  # Linux
    echo -n $MYAPIKEY | base64 -b0  # MacOS
   ```

3. Update the `docker-secret.yaml` file with your base64 encoded password. You can find the password field near the end of the file. Username \(`aWFtYXBpa2V5=`\) is already provided for you. Replace `<base_64_encoded_api_key_value>` with your own base64 encoded apikey value, and ensure you've saved the file.
4. Apply the secret to your cluster:

   ```text
    kubectl apply --filename docker-secret.yaml
   ```

5. A `Service Account` provides an identity for processes that run in a Pod. This Service Account will be used to link the build process for Knative to the Secrets you just created. View the service account file, and notice that it's using the credentials you created earlier for pulling from and pushing to the container registry:

   ```text
    cat service-account.yaml
   ```

   Example output:

   ```yaml
     apiVersion: v1
     kind: ServiceAccount
     metadata:
       name: build-bot
     secrets:
     - name: ibm-cr-push-secret
     imagePullSecrets:
     - name: ibm-cr-secret
   ```

6. Apply the service account to your cluster:

   ```text
    kubectl apply --filename service-account.yaml
   ```

Congratulations! You've set up some required credentials that the Tekton pipeline process will use to have access to push to your container image registry. In the next exercise, you will build the image, push it to the registry, and then deploy the app to knative using Tekton Pipelines. The goal of this exercise was to set up some required credentials for that flow.

Continue on to [exercise 7](exercise-7.md).

