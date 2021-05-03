# Challenge 4: Automate deployment of your containers to AKS

**[Home](../README.md)** 

## Introduction

You've built your containers and pushed them to ACR. Now we can automate the process of pulling those containers from ACR and running them in your Kubernetes cluster!

## Description
Review the Kubernetes manifests in the `deploy` folders of the two applications. These manifests control how your application is going to run in Kubernetes. We're going to use an Azure DevOps pipeline to apply these manifests in your cluster, just like you did on the command line in earlier exercises!

These manifests being in source control means that there is a single source of truth describing how your containers run -- they are versioned, repeatable, and can easily be rolled back or rolled forward!

Simply open `variables.user.yml` and set `deployAfterBuild` to true for both projects' pipelines, then commit the change. You should see a build kick off immediately.

## Success Criteria

Your pipelines run successfully and you can see the containers running in your AKS cluster. If you look at the pods with `kubectl describe`, you should see annotations indicating what version of the container is running.

## Hints

If you have existing containers deployed to your cluster, you may be low on available resources, which can cause the deployment to time out!

You can clean up your cluster's existing deployments and services for the `content-web` and `content-api` applications by running the following commands:

``kubectl delete deploy --selector=app=content-api -n default`
``kubectl delete deploy --selector=app=content-web -n default`
``kubectl delete svc --selector=app=content-api -n default`
``kubectl delete svc --selector=app=content-web -n default`

If you deployed your resources to a different namespace, just replace `default` with the namespace name.
