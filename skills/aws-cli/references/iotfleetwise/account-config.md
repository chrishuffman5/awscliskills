# Account & Configuration

### 8.1 `register-account`

Registers your AWS account for IoT FleetWise. Required before using the service.

**Synopsis:**
```bash
aws iotfleetwise register-account \
    [--timestream-resources <value>] \
    [--iam-resources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--timestream-resources` | No | structure | None | Timestream database and table (deprecated) |
| `--iam-resources` | No | structure | None | IAM role for Timestream access (deprecated) |

**TimestreamResources:**
```json
{
    "timestreamDatabaseName": "string",
    "timestreamTableName": "string"
}
```

**IamResources:**
```json
{
    "roleArn": "string"
}
```

> **Note:** Timestream resources are deprecated. Register without them and pass data destinations directly to `create-campaign`.

**Output Schema:**
```json
{
    "registerAccountStatus": "REGISTRATION_SUCCESS|REGISTRATION_PENDING|REGISTRATION_FAILURE",
    "timestreamResources": {
        "timestreamDatabaseName": "string",
        "timestreamTableName": "string"
    },
    "iamResources": {
        "roleArn": "string"
    },
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 8.2 `get-register-account-status`

Retrieves account registration status.

**Synopsis:**
```bash
aws iotfleetwise get-register-account-status \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "customerAccountId": "string",
    "accountStatus": "REGISTRATION_SUCCESS|REGISTRATION_PENDING|REGISTRATION_FAILURE",
    "timestreamRegistrationResponse": {
        "timestreamDatabaseName": "string",
        "timestreamTableName": "string",
        "timestreamDatabaseArn": "string",
        "timestreamTableArn": "string",
        "registrationStatus": "REGISTRATION_SUCCESS|REGISTRATION_PENDING|REGISTRATION_FAILURE"
    },
    "iamRegistrationResponse": {
        "roleArn": "string",
        "registrationStatus": "REGISTRATION_SUCCESS|REGISTRATION_PENDING|REGISTRATION_FAILURE"
    },
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 8.3 `put-encryption-configuration`

Sets encryption configuration for IoT FleetWise data.

**Synopsis:**
```bash
aws iotfleetwise put-encryption-configuration \
    --encryption-type <value> \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--encryption-type` | **Yes** | string | -- | `KMS_BASED_ENCRYPTION` or `FLEETWISE_DEFAULT_ENCRYPTION` |
| `--kms-key-id` | No | string | None | KMS key ID (required if KMS_BASED_ENCRYPTION) |

**Output Schema:**
```json
{
    "kmsKeyId": "string",
    "encryptionStatus": "PENDING|SUCCESS|FAILURE",
    "encryptionType": "KMS_BASED_ENCRYPTION|FLEETWISE_DEFAULT_ENCRYPTION"
}
```

---

### 8.4 `get-encryption-configuration`

Retrieves encryption configuration.

**Synopsis:**
```bash
aws iotfleetwise get-encryption-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "kmsKeyId": "string",
    "encryptionStatus": "PENDING|SUCCESS|FAILURE",
    "encryptionType": "KMS_BASED_ENCRYPTION|FLEETWISE_DEFAULT_ENCRYPTION",
    "errorMessage": "string",
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 8.5 `put-logging-options`

Sets logging options for IoT FleetWise.

**Synopsis:**
```bash
aws iotfleetwise put-logging-options \
    --cloud-watch-log-delivery <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cloud-watch-log-delivery` | **Yes** | structure | -- | CloudWatch Logs delivery configuration |

**CloudWatchLogDelivery:**
```json
{
    "logType": "OFF|ERROR",
    "logGroupName": "/aws/iotfleetwise/logs"
}
```

**Output:** None

---

### 8.6 `get-logging-options`

Retrieves logging options.

**Synopsis:**
```bash
aws iotfleetwise get-logging-options \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "cloudWatchLogDelivery": {
        "logType": "OFF|ERROR",
        "logGroupName": "string"
    }
}
```
