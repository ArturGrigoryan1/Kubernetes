# Task 2 with ExternalName

This project demonstrates how to deploy a Kubernetes Pod and Service that redirects to an external endpoint using `kubectl`.

## Prerequisites

Make sure you have `kubectl` installed and configured to connect to your Kubernetes cluster.

## Usage

Follow these steps to deploy and access the external service:

1. Apply the namespace configuration:
   
   ```bash
   kubectl apply -f external-namespace.yaml
2. Deploy the Pod that connects to the external service:
   ```bash
   kubectl apply -f external-pod.yaml
3. Create the Service that points to the external endpoint:
   ```bash
   kubectl apply -f external-service.yaml
4. Verify the Pod and Service are running:
   ```bash
   kubectl get pods -n external-namespace
   kubectl get svc -n external-namespace
5. Access the external service using the service's ClusterIP:
   The Service external is configured as an ExternalName type, redirecting to www.google.com.

## Cleanup

Don't forget to clean up after you're done testing:

```bash
kubectl delete -f external-service.yaml
kubectl delete -f external-pod.yaml
kubectl delete -f external-namespace.yaml

