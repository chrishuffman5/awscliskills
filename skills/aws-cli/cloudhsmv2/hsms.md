# HSMs

### 2.1 `create-hsm`

Creates a new HSM instance in the specified CloudHSM cluster. The cluster must be in an initialized or active state.

**Synopsis:**
```bash
aws cloudhsmv2 create-hsm \
    --cluster-id <value> \
    --availability-zone <value> \
    [--ip-address <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | ID of the cluster |
| `--availability-zone` | **Yes** | string | -- | AZ for the HSM (e.g., `us-east-1a`) |
| `--ip-address` | No | string | Auto-assigned | Specific IP address for the HSM ENI |

**Output Schema:**
```json
{
    "Hsm": {
        "AvailabilityZone": "string",
        "ClusterId": "string",
        "SubnetId": "string",
        "EniId": "string",
        "EniIp": "string",
        "EniIpV6": "string",
        "HsmId": "string",
        "HsmType": "string",
        "State": "CREATE_IN_PROGRESS",
        "StateMessage": "string"
    }
}
```

---

### 2.2 `delete-hsm`

Deletes the specified HSM from its cluster. You must specify exactly one of `--hsm-id`, `--eni-id`, or `--eni-ip`.

**Synopsis:**
```bash
aws cloudhsmv2 delete-hsm \
    --cluster-id <value> \
    [--hsm-id <value>] \
    [--eni-id <value>] \
    [--eni-ip <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | ID of the cluster containing the HSM |
| `--hsm-id` | No* | string | None | ID of the HSM to delete |
| `--eni-id` | No* | string | None | ENI ID of the HSM to delete |
| `--eni-ip` | No* | string | None | IP address of the HSM to delete |

*Exactly one of `--hsm-id`, `--eni-id`, or `--eni-ip` must be specified.

**Output Schema:**
```json
{
    "HsmId": "string"
}
```
