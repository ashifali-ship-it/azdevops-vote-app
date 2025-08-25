*****************************************************************************************



# Example Voting App with DevOps CI/CD

![Azure DevOps](https://img.shields.io/badge/Azure%20DevOps-pipelines-blue?logo=azuredevops)
![Docker](https://img.shields.io/badge/Docker-Containers-blue?logo=docker)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Cluster-blue?logo=kubernetes)
![ArgoCD](https://img.shields.io/badge/ArgoCD-GitOps-red?logo=argocd)

A simple distributed microservices application running across multiple Docker containers, with a full **DevOps CI/CD and GitOps workflow** implemented on **Azure DevOps** and **ArgoCD**.

## Application Overview

The Voting App consists of multiple services:

* A front-end web app in [Python](/vote) which lets users vote between two options
* [Redis](https://hub.docker.com/_/redis/) for queuing votes
* A [.NET](/worker) worker which processes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/) database
* A [Node.js](/result) web app showing real-time voting results

This project demonstrates Kubernetes, and microservices concepts, along with a full **CI/CD pipeline**.

---



