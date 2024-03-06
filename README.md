# AI-Planet-DevOps-Internship-Assignment

## Overview

This repository contains the DevOps internship assignment for AI Planet. It includes Kubernetes deployment configurations for an e-commerce application along with an ArgoCD application definition for continuous deployment.

## Deployment Configuration

### Deployment

The `deployment.yaml` file defines a Kubernetes Deployment for the `myapp` service. It specifies the number of replicas, container image, ports, and a canary deployment strategy with gradual weight adjustments.

### Service

The Kubernetes Service configuration in `deployment.yaml` exposes the `myapp` deployment internally within the cluster on port 3000.

## ArgoCD Configuration

### Application

The `application.yaml` file defines an ArgoCD Application named `my-argo-application` in the `argocd` namespace. It is configured to sync with the repository's `Dev-Env` directory, targeting the HEAD revision. The destination for deployment is set to the Kubernetes cluster with the specified namespace `myapp`. The sync policy includes automated options for self-healing and pruning resources.

## Usage

To deploy the application using ArgoCD, follow these steps:

1. Install ArgoCD in your Kubernetes cluster if not already installed.
2. Apply the Kubernetes manifests in the `Dev-Env` directory.
3. Create an ArgoCD Application using the `application.yaml` file provided in this repository.
4. ArgoCD will automatically sync and deploy the application based on the configuration provided.

## Running Locally on Minikube

To run the application locally on Minikube, follow these steps:

1. Start Minikube (assuming it's already installed):
   ```bash
   minikube start
   ```
2. Set up your Kubernetes context to use Minikube:
    ```bash
   kubectl config use-context minikube
   ```
3. Verify that the resources are deployed:      
    ```bash
   kubectl get deployments
   kubectl get services
   ```
4. If needed, expose the service to access it locally:
   ```bash
   minikube service myapp-service
   ```
5. To view the application on Argo CD, open a web browser and navigate to the Argo CD UI by using the following command:      
   ```bash
   minikube service argocd-server -n argocd
   ```
   This will open the Argo CD dashboard where you can view the deployed application and manage its deployment.
    These commands will deploy the application on Minikube and allow you to access it locally. Adjustments may be needed based on your specific setup and requirements.
