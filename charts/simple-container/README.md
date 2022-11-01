# simple-container

Run an existing container inside of the Imperial College London Application Platform. You have the option to bring any container image from an ICL recognised container repository and run inside of the ICL application PLatform.  

## Prerequisites (bring an existing container)

If you have your own container already witin an accesible container registry (or a 3rd party container you would like to run) then you must have access to that container repository and container image. 

Clicking on the deploy button, you will simply need to fill in the following detals:

**Name:** The name of this deployment
**Container URL:** The URL address of the container you wish to deploy
**Create Ingress:** If you would like to expose this container to an internet addressible URL
**URL Prefix:** A unique prefix for your application URL

Once filled in, click on the **Deploy** button which will set your deployment running.


## Prerequisites (build your container)

Docker
Helm

## Build

```
docker build --platform=linux/amd64 -t simple-container .
```
## Run

```
docker run -it -p 8080:8080 --rm --name simple-container ghcr.io/appvia/simple-container/simple-container:main
```

Visit http://localhost:8080 in a web browser.

## Push to GHCR

### Create a new GitHub Personal Access Token

Follow instructions as seen on:

https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry


### Push image to GHCR

```
REGISTRY=ghcr.io/appvia
GH_REPO=simple-container
IMAGE_NAME=simple-container
TAG=main
IMAGE_URL=${REGISTRY}/${GH_REPO}/${IMAGE_NAME}:${TAG}

docker build --platform=linux/amd64 -t ${IMAGE_URL} .
docker push ${IMAGE_URL}
```
