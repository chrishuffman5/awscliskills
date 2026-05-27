# Wait

Wait commands poll a resource until it reaches a desired state. Each waiter polls at a fixed interval and has a maximum number of attempts before timing out.

---

## 1. `wait endpoint-in-service`

Waits until an endpoint reaches `InService` status. Polls every 30 seconds, max 120 attempts (60 minutes).

```bash
aws sagemaker wait endpoint-in-service \
    --endpoint-name <value>
```

---

## 2. `wait endpoint-deleted`

Waits until an endpoint is deleted. Polls every 30 seconds, max 60 attempts (30 minutes).

```bash
aws sagemaker wait endpoint-deleted \
    --endpoint-name <value>
```

---

## 3. `wait notebook-instance-in-service`

Waits until a notebook instance reaches `InService` status. Polls every 30 seconds, max 60 attempts (30 minutes).

```bash
aws sagemaker wait notebook-instance-in-service \
    --notebook-instance-name <value>
```

---

## 4. `wait notebook-instance-stopped`

Waits until a notebook instance reaches `Stopped` status. Polls every 30 seconds, max 60 attempts (30 minutes).

```bash
aws sagemaker wait notebook-instance-stopped \
    --notebook-instance-name <value>
```

---

## 5. `wait notebook-instance-deleted`

Waits until a notebook instance is deleted. Polls every 30 seconds, max 60 attempts (30 minutes).

```bash
aws sagemaker wait notebook-instance-deleted \
    --notebook-instance-name <value>
```

---

## 6. `wait training-job-completed-or-stopped`

Waits until a training job reaches `Completed`, `Stopped`, or `Failed` status. Polls every 120 seconds, max 180 attempts (6 hours).

```bash
aws sagemaker wait training-job-completed-or-stopped \
    --training-job-name <value>
```

---

## 7. `wait processing-job-completed-or-stopped`

Waits until a processing job reaches `Completed`, `Stopped`, or `Failed` status. Polls every 60 seconds, max 60 attempts (60 minutes).

```bash
aws sagemaker wait processing-job-completed-or-stopped \
    --processing-job-name <value>
```

---

## 8. `wait transform-job-completed-or-stopped`

Waits until a transform job reaches `Completed`, `Stopped`, or `Failed` status. Polls every 60 seconds, max 60 attempts (60 minutes).

```bash
aws sagemaker wait transform-job-completed-or-stopped \
    --transform-job-name <value>
```

---

## 9. `wait image-created`

Waits until an image reaches `Created` status. Polls every 60 seconds, max 60 attempts (60 minutes).

```bash
aws sagemaker wait image-created \
    --image-name <value>
```

---

## 10. `wait image-updated`

Waits until an image update is complete. Polls every 60 seconds, max 60 attempts (60 minutes).

```bash
aws sagemaker wait image-updated \
    --image-name <value>
```

---

## 11. `wait image-deleted`

Waits until an image is deleted. Polls every 60 seconds, max 60 attempts (60 minutes).

```bash
aws sagemaker wait image-deleted \
    --image-name <value>
```

---

## 12. `wait image-version-created`

Waits until an image version reaches `Created` status. Polls every 60 seconds, max 60 attempts (60 minutes).

```bash
aws sagemaker wait image-version-created \
    --image-name <value> \
    [--version <value>] \
    [--alias <value>]
```

---

## 13. `wait image-version-deleted`

Waits until an image version is deleted. Polls every 60 seconds, max 60 attempts (60 minutes).

```bash
aws sagemaker wait image-version-deleted \
    --image-name <value> \
    [--version <value>] \
    [--alias <value>]
```
