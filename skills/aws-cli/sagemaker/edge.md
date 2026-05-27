# Edge

## Device Fleets

### 1. `create-device-fleet`

Creates a fleet of edge devices for deploying models.

```bash
aws sagemaker create-device-fleet \
    --device-fleet-name <value> \
    --output-config <value> \
    [--role-arn <value>] \
    [--description <value>] \
    [--enable-iot-role-alias | --no-enable-iot-role-alias] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--device-fleet-name` | **Yes** | string | -- | Fleet name (1-63 chars) |
| `--output-config` | **Yes** | structure | -- | `S3OutputLocation`, `KmsKeyId`, `PresetDeploymentType`, `PresetDeploymentConfig` |
| `--role-arn` | No | string | -- | IAM role ARN |
| `--description` | No | string | -- | Description |
| `--enable-iot-role-alias` | No | boolean | -- | Enable IoT role alias |
| `--tags` | No | list | -- | Key-value tags |

**Output:** None

---

### 2. `describe-device-fleet` / `list-device-fleets` / `update-device-fleet` / `delete-device-fleet`

```bash
aws sagemaker describe-device-fleet --device-fleet-name <value>
aws sagemaker list-device-fleets [--creation-time-after <value>] [--creation-time-before <value>] [--name-contains <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-device-fleet --device-fleet-name <value> --output-config <value> [--role-arn <value>] [--description <value>] [--enable-iot-role-alias | --no-enable-iot-role-alias]
aws sagemaker delete-device-fleet --device-fleet-name <value>
```

### 3. `get-device-fleet-report`

Gets a summary report for a device fleet.

```bash
aws sagemaker get-device-fleet-report --device-fleet-name <value>
```

---

## Devices

### 4. `register-devices`

Registers devices with a fleet.

```bash
aws sagemaker register-devices \
    --device-fleet-name <value> \
    --devices <value> \
    [--tags <value>]
```

**Device Structure:**
```json
[
    {
        "DeviceName": "string",
        "Description": "string",
        "IotThingName": "string"
    }
]
```

**Output:** None

---

### 5. `describe-device` / `list-devices` / `update-devices` / `deregister-devices`

```bash
aws sagemaker describe-device --device-name <value> --device-fleet-name <value> [--next-token <value>]
aws sagemaker list-devices [--device-fleet-name <value>] [--model-name <value>] [--latest-heartbeat-after <value>]
aws sagemaker update-devices --device-fleet-name <value> --devices <value>
aws sagemaker deregister-devices --device-fleet-name <value> --device-names <value>
```

---

## Edge Deployment Plans

### 6. `create-edge-deployment-plan`

Creates an edge deployment plan for deploying models to edge devices.

```bash
aws sagemaker create-edge-deployment-plan \
    --edge-deployment-plan-name <value> \
    --model-configs <value> \
    --device-fleet-name <value> \
    [--stages <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--edge-deployment-plan-name` | **Yes** | string | -- | Plan name (1-63 chars) |
| `--model-configs` | **Yes** | list | -- | `[{ModelHandle, EdgePackagingJobName}]` |
| `--device-fleet-name` | **Yes** | string | -- | Device fleet name |
| `--stages` | No | list | -- | Deployment stages |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "EdgeDeploymentPlanArn": "string"
}
```

---

### 7. `describe-edge-deployment-plan` / `list-edge-deployment-plans` / `delete-edge-deployment-plan`

```bash
aws sagemaker describe-edge-deployment-plan --edge-deployment-plan-name <value>
aws sagemaker list-edge-deployment-plans [--creation-time-after <value>] [--creation-time-before <value>] [--name-contains <value>] [--device-fleet-name-contains <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker delete-edge-deployment-plan --edge-deployment-plan-name <value>
```

---

### 8. `create-edge-deployment-stage` / `start-edge-deployment-stage` / `stop-edge-deployment-stage` / `delete-edge-deployment-stage`

```bash
aws sagemaker create-edge-deployment-stage --edge-deployment-plan-name <value> --stages <value>
aws sagemaker start-edge-deployment-stage --edge-deployment-plan-name <value> --stage-name <value>
aws sagemaker stop-edge-deployment-stage --edge-deployment-plan-name <value> --stage-name <value>
aws sagemaker delete-edge-deployment-stage --edge-deployment-plan-name <value> --stage-name <value>
```

---

## Edge Packaging Jobs

### 9. `create-edge-packaging-job`

Creates a packaging job to compile a model for edge deployment.

```bash
aws sagemaker create-edge-packaging-job \
    --edge-packaging-job-name <value> \
    --compilation-job-name <value> \
    --model-name <value> \
    --model-version <value> \
    --role-arn <value> \
    --output-config <value> \
    [--resource-key <value>] \
    [--tags <value>]
```

**Output:** None

---

### 10. `describe-edge-packaging-job` / `list-edge-packaging-jobs` / `stop-edge-packaging-job`

```bash
aws sagemaker describe-edge-packaging-job --edge-packaging-job-name <value>
aws sagemaker list-edge-packaging-jobs [--creation-time-after <value>] [--creation-time-before <value>] [--name-contains <value>] [--model-name-contains <value>] [--status-equals <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker stop-edge-packaging-job --edge-packaging-job-name <value>
```
