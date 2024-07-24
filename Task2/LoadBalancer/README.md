# Task 2 with LoadBalancer

This repository provides configurations to set up a simple load balancer using MetalLB in Kubernetes. MetalLB extends Kubernetes with a load-balancer implementation that doesn't require cloud provider-specific configurations.

## Prerequisites

Before you begin, ensure you have the following:
- Kubernetes cluster running
- `kubectl` configured to manage your cluster

## Installation

1. **Install MetalLB:**
   MetalLB is required to provide load balancing services within your Kubernetes cluster.

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/namespace.yaml
   kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/metallb.yaml
2. Apply Configuration:
   Apply the IP address pool and L2 advertisement configurations.
   ```bash
   kubectl apply -f ipaddresspool.yaml
   kubectl apply -f l2advertisement.yaml
3. Deploy Pods:
   Deploy the pods that will serve as endpoints behind the load balancer.
   ```bash
   kubectl apply -f load-pod1.yaml
   kubectl apply -f load-pod2.yaml
## Verification

To verify that MetalLB is configured correctly, use the following commands:
  ```bash
  kubectl get ipaddresspool.metallb.io -n metallb-system
  kubectl get l2advertisement.metallb.io -n metallb-system
  ```

## Testing the Load Balancer

Once deployed, you can test the load balancer by accessing the pods through the load balancer's external IP.

Assuming the external IP of the load balancer is <lb-external-ip>, you can test it using curl:

  ```bash
  curl http://<lb-external-ip>
  ```
## Clean Up

To remove the setup, delete the resources:

  ```bash
  kubectl delete -f load-pod1.yaml
  kubectl delete -f load-pod2.yaml
  kubectl delete -f l2advertisement.yaml
  kubectl delete -f ipaddresspool.yaml
  kubectl delete -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/metallb.yaml
  kubectl delete -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/namespace.yaml









