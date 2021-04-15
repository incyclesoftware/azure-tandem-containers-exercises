# Challenge 2: Coach's Guide

**[Home](../README.md)** - [Next Challenge >](./03-buildcontainers.md)

## Notes & Guidance
Both service connection types have a radio button for "AKS" or "ACR" (depending on type of connection). This may or may not work depending on how they're authenticated to Azure and what level of permissions they have. If this option works, it's by far the easiest. If it doesn't...

### ACR
Get credentials:
`az acr update -n [acr-name] --admin-enabled true`
`az acr credential show -n [acr-name] -g [resource-group]`

Service connection settings:
- Registry type: *Others* 
- Docker Registry: [acr-name].azurecr.io
- Username/password: credentials from above

### AKS
Get credentials
`az aks get-credentials --admin -n [cluster-name] -g [resource-group] -f -`

- Connection type: KubeConfig
- Kubeconfig: run the command, grab the huge blob of text and paste it in