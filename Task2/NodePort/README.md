# Task 2 with NodePort

This repository provides configurations to deploy a Kubernetes Namespace, Pod, and NodePort Service.

## Files Included

- `node-namespace.yaml`: Defines the Kubernetes Namespace.
- `node-pod.yaml`: Defines the Kubernetes Pod within the specified Namespace.
- `node-service.yaml`: Defines the Kubernetes NodePort Service within the specified Namespace.

## Setup Instructions

1. Apply Namespace

   Apply the `node-namespace.yaml` to create a dedicated Namespace:

   ```bash
   kubectl apply -f node-namespace.yaml
   ```
2. Deploy Pod
   Deploy the Pod node-pod.yaml into the node-namespace Namespace:
   ```bash
   kubectl apply -f node-pod.yaml
3. Create NodePort Service
   Create the NodePort Service node-service.yaml within the node-namespace Namespace:
   ```bash
   kubectl apply -f node-service.yaml

## Accessing the Service

Once deployed, the Service will be accessible on each Node's IP at the nodePort specified (31000 in this example).

To find the IP address of your nodes, use:
```bash
kubectl get nodes -o wide
```
To access the service, use one of the node's IP addresses and the nodePort (31000 in this case):
```bash
curl http://<node-ip>:31000
```
## Cleaning Up

To remove the resources created by this example, delete them using kubectl delete:

```bash
kubectl delete -f node-service.yaml
kubectl delete -f node-pod.yaml
kubectl delete -f node-namespace.yaml
```
