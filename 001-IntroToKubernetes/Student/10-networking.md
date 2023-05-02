# Challenge 10: Networking

[< Previous Challenge](./09-helm.md) - **[Home](../README.md)** - [Next Challenge >](./11-opsmonitoring.md)

## Introduction

We started out with some very simple, default networking that Kubernetes gives us for free. But this is rarely what we'll need to go into production. Now we'll get a little more in depth on networking in Kubernetes

## Description

In this challenge you will be installing an Ingress Controller and learning how the "Ingress" resource in Kubernetes works. 

- Delete the existing content-web deployment and service.
- Install the App Gateway ingress controller using the Azure Portal.
- Deploy the content-web service and create an Ingress resource for it. 
	- The reference template can be found in the Challenge 10 Resources folder: `template-web-ingress-deploy.yaml`
	- Change the ACR DNS Name to match yours.
- Access the application by the app gateway's IP address (`kubectl get ingress`)

## Success Criteria

1. The App Gateway Ingress Controller is installed in your cluster
1. You've recreated a new Ingress for content-web that allows access through an app gateway IP address