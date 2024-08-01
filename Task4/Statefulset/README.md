# StatefulSet Configuration

This document provides details and instructions for deploying a StatefulSet using the provided `statefulset.yaml` file.

## Deployment Instructions

1. **Save the YAML File**: Save the YAML configuration to a file named `statefulset.yaml`.

2. **Apply the Configuration**: Use `kubectl` to apply the configuration:
```sh
kubectl apply -f statefulset.yaml
```
3. **Verify Deployment**:
### Check the StatefulSet status:
```sh
kubectl get statefulsets
```
### Verify the Pods are running:
```sh
kubectl get pods
```
### Check the Persistent Volume Claims:
```sh
kubectl get pvc
```
4. **Access Logs**:To view logs from a specific Pod, use:
```sh
kubectl logs <pod-name>
```
5. **Troubleshooting**:If you encounter issues, describe the StatefulSet or Pod for more details:
```sh
kubectl describe statefulset myapp
kubectl describe pod <pod-name>
```
