# Challenge 3: Coach's Guide

[< Previous Challenge](./02-acr.md) - **[Home](README.md)** - [Next Challenge >](./04-k8sdeployment.md)

## Notes & Guidance

- Remind teams that kubectl can be installed through the CLI, but don’t give away the answer:
	- `az aks install-cli`
	- Note that WSL users will have to alias the Windows location of Kubectl afterwards:
		- `alias kubectl=/mnt/c/users/<your username>/.azure-kubectl/kubectl.exe`
- All teams should have an AKS cluster stood up relatively quickly but they will likely need some hints regarding the correct parameters for the `az aks create` command.
	- The default Kubernetes version used by the az aks create command should be fine.  
	- The CLI should be used to create the cluster to give the most realistic experience.  
	- Cluster names should be unique within the subscription.  
	- Here’s an example command that creates a cluster named **wth-aks02-poc** in resource group **wth-rg02-poc:** using basic networking, managed identity, 3 nodes in separate availability zones and an attached ACR:
		- `az aks create --location eastus --name wth-aks02-poc --node-count 3  --no-ssh-key --resource-group wth-rg02-poc --zones 1 2 3 --enable-managed-identity --attach-acr <acrname>`
    - Documentation on installing AKS can be found here:
		- [Portal](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough-portal)
		- [CLI](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough)
- It is usually a good idea to explain to the students what kind of options they have when creating a cluster. Doing a walkthrough demo of provisioning a cluster with the Portal is good showcasing tool, but end by telling them they need to figure out how to achieve the same thing with the CLI.
- Have the teams show you the running cluster with:
	- `kubectl get nodes --show-labels`
		- It should 3 nodes with each node in a different availability zone.  
	- Each node should be a VM with at least 2 vCPU and 4 GB of memory.  The reason for this is that we need to have enough CPU and RAM for the system pods to run (e.g. CoreDNS and tunnelfront).  See this link for more details: 
    	- <https://docs.microsoft.com/en-us/azure/aks/use-system-pools>
	- **NOTE:** They will need to learn how to connect kubectl to their cluster using `az aks get-credentials`
- If someone needs to attach their ACR to the cluster after they created it, they can use: 
	- `az aks update -n myAKSCluster -g myResourceGroup --attach-acr <acrName>`
- **Optional:** The Kubernetes dashboard can be brought up with the CLI easily:
	- `az aks browse --name myAKSCluster --resource-group myAKSCluster`
	- **NOTE:** For the dashboard to work properly, it requires more permissions than those enabled by default for the account that the cluster uses. More info about this can be found here: 
    	- <https://blog.jcorioland.io/archives/2018/08/29/azure-aks-rbac-kubernetes-dashboard.html>