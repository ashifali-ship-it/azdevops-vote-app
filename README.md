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

## Table of Contents

- [Overview](#overview)  
- [Getting Started](#getting-started)  
  - [Kubernetes Deployment](#run-the-app-in-kubernetes)  
- [Architecture](#architecture)  
- [CI/CD & GitOps Workflow](#cicd--gitops-workflow)  
- [Notes](#notes)  

---

## Overview

This solution demonstrates:

- **Languages & frameworks:** Python, Node.js, .NET  
- **Messaging:** Redis  
- **Persistent storage:** PostgreSQL  
- **Orchestration:** Kubernetes  
- **CI/CD:** Azure DevOps Pipelines  
- **GitOps:** ArgoCD  

---

## Getting Started

### Run the App in Kubernetes

The folder `k8s-specifications/` contains YAML definitions for deployments and services.

Deploy the app:

```bash
kubectl create -f k8s-specifications/

```
Delete resources:
```bash
kubectl delete -f k8s-specifications/
```
## Architecture

## Architecture Diagram

![Project Architecture](az-gitops%20project%20architecture.PNG)

**Components:**

- **Vote App (Python)** – Frontend for voting  
- **Redis** – Queues votes for processing  
- **Worker App (.NET)** – Processes votes and updates Postgres  
- **PostgreSQL** – Persistent database  
- **Result App (Node.js)** – Shows real-time voting results  

---

## CI/CD & GitOps Workflow

This project demonstrates **Azure DevOps Pipelines and GitOps deployment**:

### Source Code Management
- **Azure Repos**

### CI Pipelines
Separate pipelines for `vote`, `worker`, and `result` apps

**Stages:**

- **Build** – Builds Docker images  
- **Push** – Pushes images to **Azure Container Registry (ACR)**  
- **Test** – Runs simple smoke tests  
- **Update** – Updates Kubernetes deployment YAML with new image tags  

### CD with ArgoCD
- Monitors Git repository  
- Deploys updated manifests automatically to the Kubernetes cluster  

**Workflow:**

1. Developer commits code → Azure DevOps pipeline triggers  
2. Docker image is built and pushed to **ACR**  
3. Deployment YAML is updated with new image tag  
4. ArgoCD detects change → synchronizes Kubernetes cluster with the repo  
5. App is updated seamlessly in the cluster  

This approach demonstrates **GitOps principles**, ensuring **version-controlled deployments and automated rollouts**.  

---

## Notes

- Each client can vote only once per browser session  
- This project is an **educational sample**, not production-ready  
- Designed to demonstrate **multi-language microservices, Kubernetes, CI/CD, and GitOps integration**
