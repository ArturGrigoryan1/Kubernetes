# DaemonSet Configuration

This document explains a Kubernetes DaemonSet configuration. A DaemonSet ensures that a specific container runs on every node in the Kubernetes cluster.

## Usage

1. **Create the DaemonSet**:
   Apply the configuration using `kubectl`:
   ```sh
   kubectl apply -f <path-to-your-ds.yaml>
2. **Verify the DaemonSet**:
   Check the status of the DaemonSet:
   ```sh
   kubectl get daemonsets
3. **View Pod Details**:
   List the Pods created by the DaemonSet:
   ```sh
   kubectl get pods -l <label-selector>
4. **View Pod Logs**:
   To see the output from the DaemonSet, find the corresponding Pod and view its logs:
   ```sh
   kubectl logs <pod-name>
