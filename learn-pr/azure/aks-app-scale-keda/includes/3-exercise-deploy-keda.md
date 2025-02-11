## Install the `aks-preview` Azure CLI extension

1. Install the `aks-preview` extension using the `az extension add` command.

    ```azurecli-interactive
    az extension add --name aks-preview
    ```

2. Update to the latest version of the `aks-preview` extension using the `az extension update` command.

    ```azurecli-interactive
    az extension update --name aks-preview
    ```

## Register the `AKS-KedaPreview` feature flag

1. Register the `AKS-KedaPreview` feature flag using the `az feature register` command.

    ```azurecli-interactive
    az feature register --name AKS-KedaPreview --namespace Microsoft.ContainerService
    ```

    It takes a few minutes for the status to show as *Registered*.

2. Verify the registration status using the `az feature show` command.

    ```azurecli-interactive
    az feature show --name AKS-KedaPreview --namespace Microsoft.ContainerService
    ```

3. When the status reflects as *Registered*, refresh the registration of the Microsoft.ContainerService resource provider using the `az provider register` command.

    ```azurecli-interactive
    az provider register --namespace Microsoft.ContainerService
    ```

## Enable the KEDA add-on on an AKS cluster

1. Open the [Azure Cloud Shell](https://shell.azure.com) in your browser and select **Bash**.
2. Create environment variables for the resource group name, location, and cluster name for use throughout this module. If you want to use your own names or location, replace the values in the following commands with your own.

    ```azurecli-interactive
    RESOURCE_GROUP=myContosoRG
    LOCATION=westus2
    CLUSTER_NAME=myContosoCluster
    ```

3. Create an Azure resource group using the `az group create` command.

    ```azurecli-interactive
    az group create -n $RESOURCE_GROUP -l $LOCATION
    ```

4. Create an AKS cluster with the KEDA add-on enabled using the `az aks create` command and the `--enable-keda` flag.

    ```azurecli-interactive
    az aks create -g $RESOURCE_GROUP -n $CLUSTER_NAME --enable-keda --generate-ssh-keys
    ```

5. Connect to your AKS cluster using the `az aks get-credentials` command.

    ```azurecli-interactive
    az aks get-credentials -n $CLUSTER_NAME -g $RESOURCE_GROUP
    ```

6. Verify the KEDA add-on is installed on your cluster using the `az aks show` command and set the `--query` flag to `workloadAutoScalerProfile.keda.enabled`.

    ```azurecli-interactive
    az aks show -n $CLUSTER_NAME -g $RESOURCE_GROUP --query "workloadAutoScalerProfile.keda.enabled"
    ```

    Your output should look like the following example output, which shows the KEDA add-on is installed on the cluster:

    ```output
    true
    ```

## Create an Azure Cache for Redis instance

1. Create an environment variable for the Redis name for use throughout this module.

    ```azurecli-interactive
    REDIS_NAME=contoso-redis-$RANDOM
    ```

2. Create an Azure Cache for Redis instance using the `az redis create` command.

    ```azurecli-interactive
    az redis create --location $LOCATION --name $REDIS_NAME --resource-group $RESOURCE_GROUP --sku Basic --vm-size c0 --enable-non-ssl-port
    ```

3. Create environment variables for the Redis host and key for use throughout this module using the `az redis show` and `az redis list-keys` commands.

    ```azurecli-interactive
    REDIS_HOST=$(az redis show -n $REDIS_NAME -g $RESOURCE_GROUP -o tsv --query "hostName")
    REDIS_KEY=$(az redis list-keys --name $REDIS_NAME --resource-group $RESOURCE_GROUP -o tsv --query "primaryKey")
    ```
