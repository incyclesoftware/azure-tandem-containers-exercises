# Challenge 11: Operations and Monitoring

[< Previous Challenge](./10-networking.md) - **[Home](../README.md)**

## Introduction

Running a cluster without knowing what is going on inside of it is a show-stopper for any serious production deployment. It is imperative that we are familiar with operationalizing our Kubernetes clusters and having a full view into day to day running and error state alerts.

## Description

In this challenge you will learn how to view application logs and trouble-shoot errors. View performance metrics and identity bottlenecks.

- Find the logs for your application’s containers, using:
	- `kubectl`
	- Using the Kubernetes Dashboard
	- Notice how you can check the logs of any of your pods individually.
- Start a bash shell into one of the containers running on a pod and check the list of running processes
- Find out if your pods had any errors.
	- Figure out how to get details on a running pod to see reasons for failures.
- Azure Monitor:
	- Enable "Azure Monitor for Containers" on the AKS cluster
	- Show a screenshot of CPU and memory utilization of all nodes
	- Show a screenshot displaying logs from the frontend and backend containers

## Success Criteria

1. Show logs for the containers running in your cluster.
2. Log into a running container and issue bash commands.
3. Show Azure Monitor working.

## Learning Resources
- Azure Monitoring for Containers:
    - <https://docs.microsoft.com/en-us/azure/azure-monitor/insights/container-insights-overview>
