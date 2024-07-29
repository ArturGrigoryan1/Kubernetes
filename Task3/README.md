# Task 3 Kubernetes Deployment 

This document provides instructions for deploying MongoDB and a web application using Kubernetes manifests. This example is taken from the TechWorld with Nana course. Follow these steps to set up your environment.

## Prerequisites

- Ensure you have Kubernetes cluster access and `kubectl` installed.
- Ensure Docker is installed if you want to build or modify container images.
- Ensure you have the `mongo-config.yaml`, `mongo-secret.yaml`, `mongo.yaml`, and `webapp.yaml` files.

## Deployment Steps

### 1. Apply Configuration and Secrets

First, you need to apply the configuration and secrets for MongoDB:

```sh
kubectl apply -f mongo-config.yaml
kubectl apply -f mongo-secret.yaml
```
These files define the MongoDB configuration and credentials required for the deployment.
### 2.Deploy MongoDB
Next, deploy the MongoDB instance:
```sh
kubectl apply -f mongo.yaml
```
This file creates a MongoDB deployment and a corresponding service to expose MongoDB.
### 3.Deploy the Web Application
Finally, deploy the web application:
```sh
kubectl apply -f webapp.yaml
```
This file creates a deployment and a service for the web application, configuring it to connect to MongoDB using the provided environment variables.

## Accessing the Web Application

After deploying the web application, it will be accessible via a NodePort service. Use the following command to get the external IP and port:

```sh
kubectl get services
```
Look for the webapp-service and note the NodePort value. You can access the web application in your browser at http://<node-ip>:<node-port>.

## Troubleshooting

### Check the status of your pods and services using
```sh 
kubectl get pods
kubectl get services
```
### To view logs for a pod, use
```sh
kubectl logs <pod-name>
```
### For more details on a specific resource, use
```sh
kubectl describe <resource> <resource-name>
```
## Cleaning Up
To delete all resources created, you can use the following commands
```sh
kubectl delete -f webapp.yaml
kubectl delete -f mongo.yaml
kubectl delete -f mongo-secret.yaml
kubectl delete -f mongo-config.yaml
```
