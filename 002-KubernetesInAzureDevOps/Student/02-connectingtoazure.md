# Challenge 2: Connecting Azure DevOps to Azure

**[Home](../README.md)** - [Next Challenge >](./03-buildcontainers.md)

## Introduction

Azure DevOps needs to be able to communicate with your container registry and Kubernetes cluster. In this exercise, you'll be creating *service connections* so that 

Azure DevOps knows how to authenticate with your ACR and AKS instances.

## Description
Navigate to the "Service Connections" section in the Project Settings page of your Azure DevOps project.

Add a "Kubernetes" type service connection to Azure DevOps

Add a "Docker Registry" type service connection to Azure DevOps


## Success Criteria

You have a service connection for a container registry

You have a service connection for a Kubernetes cluster

## Hints
There are a number of different ways to get credentials for both (CLI, Azure portal). All are valid!

You may need to enable admin credentials for ACR