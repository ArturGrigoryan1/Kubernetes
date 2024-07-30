# CronJob Configuration

This repository contains a Kubernetes `CronJob` configuration file. The CronJob runs a simple job that prints a message to the console every minute. Below is a detailed explanation of the configuration options used in the CronJob.

## Explanation

### `schedule`

The `schedule` field defines the cron schedule for the CronJob. This is a standard cron format used to specify the time and frequency of job execution.

- **Format**: `* * * * *`
  - **Minutes**: `*` (every minute)
  - **Hours**: `*` (every hour)
  - **Day of month**: `*` (every day of the month)
  - **Month**: `*` (every month)
  - **Day of week**: `*` (every day of the week)

**Common Schedule Variants**:
- `*/5 * * * *`: Every 5 minutes.
- `0 * * * *`: At the start of every hour.
- `0 0 * * *`: Daily at midnight.
- `0 0 * * 0`: Weekly at midnight on Sundays.

### `restartPolicy`

The `restartPolicy` field determines how Kubernetes handles container restarts when a container fails.

- **OnFailure**: The container will be restarted only if it exits with a non-zero exit code (i.e., an error).
- **Always**: The container will always be restarted regardless of its exit status.
- **Never**: The container will not be restarted, regardless of its exit status.

In the provided configuration, `restartPolicy: OnFailure` means that if the command within the container fails, Kubernetes will attempt to restart it. If the command succeeds, the container will not be restarted.

### `imagePullPolicy`

The `imagePullPolicy` field specifies when Kubernetes should pull the container image.

- **Always**: Kubernetes will always pull the image from the registry before starting a container, even if the image already exists locally.
- **IfNotPresent**: Kubernetes will pull the image only if it is not already present on the node. This avoids unnecessary pulls if the image is already available.
- **Never**: Kubernetes will never pull the image from the registry, and it assumes the image is already present on the node. This is useful in environments where images are preloaded.

In the provided configuration, `imagePullPolicy: IfNotPresent` means that Kubernetes will only pull the image if it is not already present on the node.

## Usage

1. **Create the CronJob**:
   Apply the configuration using `kubectl`:
   ```sh
   kubectl apply -f <path-to-your-cj.yaml>
2.**Verify the CronJob**:
Check the status of the CronJob:
```sh
kubectl get cronjobs
```
3.**View Job Execution**:
Check the jobs created by the CronJob:
```sh
kubectl get jobs --selector=job-name=<cronjob-name>
```
4.**View Pod Logs**:
To see the output from the CronJob, find the corresponding Pod and view its logs:
```sh
kubectl get pods --selector=job-name=<cronjob-name>
kubectl logs <pod-name>
```
