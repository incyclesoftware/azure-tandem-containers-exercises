# Challenge 3: Build your containers... in THE CLOUD!

**[Home](../README.md)** - [Next Challenge >](./04-runcontainers.md)

## Introduction

Now that all of your code is in Azure DevOps and you have connections to AKS and ACR set up, you can automate building and versioning your container!

This is accomplished via Azure DevOps YAML pipelines, which allow you to specify your build and deployment process as a series of sequential jobs.

## Description
Your repo already has everything you need! You'll just need to update a few files and create a new pipeline definition that points to the YAML files.
- The files `content-api/pipelines/variables.user.yml` and `content-web/pipelines/variables.user.yml` need to be updated
  - `dockerRegistryServiceConnection` - The name of your ACR service connection
  - `kubernetesServiceConnection` - The name of your AKS service connection
  - `imageRepository` - The name of the image repository in ACR that you want to push to. This can be anything you want, or you can leave it as-is.
  - `containerRegistry` - The name of your ACR, ending in `azurecr.io`. 

  Create two pipelines, pointing to `content-api/pipelines/pipeline.yml` and `content-web/pipelines/pipeline.yml`. Save them.
  These pipelines use a tool called GitVersion to automatically manage semantic version numbers. One of the drivers for the version number is the tag on the repository. For GitVersion to function properly, we'll need to ensure that the repos are tagged after a successful release.
  This is a little bit tricky to find, so the exact location is:
  - Click on a pipeline. 
  - Click  *Edit*. 
  - In the ellipsis menu next to the *Run* button, choose *Triggers*. 
  - This opens up a new page. Click the *YAML* tab
  - Click *Get Sources*
  - Change the *Tag Sources* radio button to **On success**
  - Save the pipeline


## Success Criteria

Your pipelines run successfully and you can see the versioned container in your ACR

## Hints