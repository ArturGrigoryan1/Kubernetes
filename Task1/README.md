# Our task 1

This project demonstrates how to deploy a Kubernetes pod and service using `kubectl`.

## Prerequisites

Make sure you have `kubectl` installed and configured to connect to your Kubernetes cluster.

## Usage

Follow these steps to deploy and access the application:

1. Apply the namespace configuration:
   
   ```bash
   kubectl apply -f namespace.yaml
2. Deploy the pod:
   ```bash
   kubectl apply -f pod.yaml
3. Create the service:
   ```bash
   kubectl apply -f service.yaml
4. Forward the port to access the service locally:
   ```bash
   kubectl port-forward svc/my-service 8080:80 --namespace=my-namespace
5. Open your web browser and go to http://localhost:8080/ to see the result.
