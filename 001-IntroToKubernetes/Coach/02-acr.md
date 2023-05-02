# Challenge 2: Coach's Guide

[< Previous Challenge](./01-containers.md) - **[Home](README.md)** - [Next Challenge >](./03-k8sintro.md)

## Notes & Guidance

- To create the registry from the CLI, use: 
    - `az acr create -n <name of registry> -g <resource group> --sku Standard`
- To login to the ACR, use: 
    - `az acr login --name <name of ACR>`
    - Note: If using `podman` or `nerdctl` instead of `docker`, use the following:
        - ACR_ACCESS_TOKEN=$(az acr login -n <name of ACR> --expose-token -o tsv --query accessToken)
        - podman login <name of ACR>.azurecr.io -u 00000000-0000-0000-0000-000000000000 --password-stdin <<< $ACR_ACCESS_TOKEN
- To tag images, use: 
    - `docker tag <name of image> <name of ACR>/<namespace>/<name of image>`
    - For example: 
        - `docker tag content-web peteacr01.azurecr.io/wthaks/content-web`
        - `docker tag content-api peteacr01.azurecr.io/wthaks/content-api`
- To push the docker image, use: 
    - `docker push <name of ACR>/<namespace>/<name of image> `
    - For example: 
        - `docker push peteacr01.azurecr.io/wthaks/content-web `
        - `docker push peteacr01.azurecr.io/wthaks/content-api`
- To list images in the repository, use:
    - `az acr repository list --name <name of ACR>`


