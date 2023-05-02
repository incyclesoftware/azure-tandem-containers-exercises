# Challenge 9: Coach's Guide

[< Previous Challenge](./08-storage.md) - **[Home](README.md)** - [Next Challenge >](./10-networking.md)

## Notes & Guidance
- You should deliver a demo in addition to the lecture to show what a working Helm chart looks like.
- You should provide guidance in the challenge as to which values should be parameterized in the Helm templates.
- **NOTE:** Helm 3 does not create namespaces with yaml files in the chart.
	- The YAML files in the Student Resources folder provides a YAML file that creates a whatthehack namespace. 
	- Students can not include the namespace YAML when creating the helm chart
	- They have to create the namespace by using the **--create-namespace** flag on the helm CLI, eg:
		- `helm install myrelease app-languages --create-namespace --namespace=whatthehack`
		- Upgrading from v1 to v2, etc: `helm upgrade myrelease app-languages-helm-chart --create-namespace --namespace=whatthehack --set appData.imageVersion=v1`
		- Note: may need to include a path to a kubeconfig file if running in hybrid environment (i.e. Helm installed in WSL, Kubectl in Windows): `--kubeconfig /mnt/c/users/accountname/.kube/config`

- Rollback a release: `helm rollback myrelease --namespace whatthehack`
- Consider using the helm chart provided in the Coach Solutions folder for Challenge 9 as one that can be demoed during the lecture.  
- You can also change the challenge to turn the existing YAML files for the FabMedical app they've been working on into a helm chart.  This lets the attendees build on what they have already completed.  The end result should be the same.

- Package chart:
	- `helm package`
- Login to ACR for helm:
	- `ACR_ACCESS_TOKEN=$(az acr login -n <name of ACR> --expose-token -o tsv --query accessToken)`
	- `helm registry login <ACR name>.azurecr.io --username 00000000-0000-0000-0000-000000000000 --password-stdin <<< $ACR_ACCESS_TOKEN`
- Push:
	- `helm push langfacts-0.1.0.tgz oci://<acr name>.azurecr.io/helm`	
- Use chart from registry:
	- `helm install langfactsacr oci://<acr name>.azurecr.io/helm/langfacts --version 0.1.0 --namespace whatthehack`