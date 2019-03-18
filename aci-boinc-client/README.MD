# Create a BOINC client on a Container Instance

Create a BOINC client on a Container Instance

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F201-aci-wordpress%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F201-aci-wordpress%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

This template creates a BOINC client on a Container Instance. The BOINC client content is persistently stored on an Azure Storage File Share.

`Tags: Azure Container Instance, boinc`

## Solution overview and deployed resources

The following resources are deployed as part of the solution

+ **Azure Container Instance**: Azure Container Instance to host the BOINC client.
+ **Azure Container Instance**: A [run-once](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-restart-policy#container-restart-policy) Azure Container Instance, where the az-cli is executed to create the file shares
+ **Storage Account**: Storage account for the file shares to store the BOINC client content
+ **File share**: Azure File shares to store BOINC client content.

## Deployment steps

You can click the "deploy to Azure" button at the beginning of this document or follow the instructions for command line deployment using the scripts in the root of this repo. 

#### Parameters:
+ **location**: Location of all the resouces.
+ **containerGroupName**: The name of the container group.
+ **numberCores**: The CPU request of the container instance.
+ **memoryInGB**: The memory request in GB of this container instance.
+ **gpuSku**: The SKU of the GPU resource.
+ **numberGpus**: The count of the GPU resource.
+ **storageAccountName**: The name of the storage account that contains the Azure File share.
+ **storageAccountType**: Storage Account type**
+ **fileShareName**: The name of the Azure File share to be mounted as a volume.
+ **restartPolicy**: Restart policy for all containers within the container group.
+ **allowRemoteGuiRpc**: Allows connecting to the client with any IP address.
+ **guiRpcPassword**: The password what you need to use, when you connect to the BOINC client.
+ **dnsLabel**: The Dns name label for the public IP.

#### Output:
+ **siteFQDN**: The BOINC client FQDN (e.g.  `boinc-client.westus.azurecontainer.io`)

## Usage

Use BOINC manager to access the site FQDN from deployment output. BOINC will guide you through the rest of the setup.

## Notes
Azure Container Instance is available in selected [locations](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-quotas#region-availability). Please use one of the available location for Azure Container Instance resource.