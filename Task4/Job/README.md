# Job Configuration

This repository contains an example of a Kubernetes Job configuration. A Kubernetes Job is used to run a one-time task that completes and terminates once the job is done.

## Job Configuration

The provided `job.yaml` file defines a Kubernetes Job that performs a simple task. The task involves creating a file with a message and then reading the content of that file. The Job will retry up to 5 times if it fails.

## How to Apply the Job

### To apply this Job configuration to your Kubernetes cluster, use the following command:

```sh
kubectl apply -f job.yaml
```
### To check the status of the Job, you can use:
```sh
kubectl get jobs
```
### To view detailed information about the Job, use:
```sh
kubectl describe job retry-job
```
### To view logs from the Job's Pod, you can use:
```sh
kubectl logs -l job-name=retry-job
```
