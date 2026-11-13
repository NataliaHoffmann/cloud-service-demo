# Cloud Service Demo A1
This site is built in COMP4312
Created by Natalia Hoffmann

## Project Purpose:
The purpose of this project is to learn and demonstrate how Git and GitHub support version control, Docker packages an application into a container, and Kubernetes deploys the containerized application in a cloud environment.

I used Git and GitHub to manage, track, and publish changes to my code, Docker to package the application into a container, and Kubernetes to deploy and expose the application.

## Included Files:

* `index.html`: the webpage for the Cloud Service Demo
* `README.md`: The documentation file with the title, author and class code, as well as explaining the purpose of the project, included files, version control benefits and the difference between Docker image and Docker container.
* `Dockerfile`: The text file with instructions that Docker uses to build the container image.
* `kubernetes/deployment.yaml`: The Kubernetes Deployment configuration, that runs and manages the application Pod.
* `kubernetes/service.yaml`: The Kubernetes Service configuration, that exposes the application through a NodePort.


## Version Control & Git & GitHub Benefits:
Git and GitHub are complementary tools that have an important role in software development.

* Git is a version-control tool that runs locally on your computer, providing tools for tracking changes, managing project history, working offline and creating and merging branches.
* GitHub, on the other hand, is an online platform that hosts Git repositories and supports collaboration through cloud-based code storage and project management.

Together, they are essentials to protect developers from losing their work and allowing multiple contributors to work simultaneously without interfering with each other's contributions. Branches allow team members to develop different features independently and commits record changes and provide a history of the project's progress. These features help cloud and DevOps teams collaborate efficiently, manage code changes, and maintain an organized development process.

## Docker
Docker is an open-source platform that automates the deployment, scaling, and management of applications inside lightweight, isolated packages called containers

Docker image is a read-only template that stores as a package, everything that the program needs to run: the code, libraries, dependencies and settings.

Docker container is the live version, runtime instance of a Docker image.

## Kubernetes

### Pods vs Deployment
A Pod is the smallest unit Kubernetes runs and contains one or more containers. A Deployment manages those Pods and make sure they keep executing replacing Pods if they fail or die.

### Purpose of a Kubernetes Service
Kubernetes service provides a stable network for a group of Pods and routes traffic to them.

This project uses service.yaml to expose the application on port 30080 and forward traffic to port 80.

### Why might a cloud application need more than one Pod?
Multiple Pods can handle more requests and improve availability if a Pod fails. This project's has one replica.

## How to run the application
To build the Docker image using the Dockerfile: open your terminal and run the command:

```bash
docker build -t cloud-service-demo:1.0 .
```

To run the Docker Container run the command on your terminal:
```bash
docker run -d --name cloud-demo-container -p 8080:80 cloud-service-demo:1.0
```

### Run with Kubernetes and Minikube
Start Minikube

```bash
minikube start --driver=docker
```

Load the image
```bash
minikube image load cloud-service-demo:1.0
```

Apply the Kubernetes Deployment and Service:
```bash
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

Forward the Service to port 8080 on your computer.
```bash
kubectl port-forward service/cloud-service-demo 8080:80
```

Keep this command running, then open <a href="http://localhost:8080">http://localhost:8080</a> on your preferred browser.