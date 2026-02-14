# Instances

### 1.1 `create-instance`

Creates an Amazon Connect instance.

**Synopsis:**
```bash
aws connect create-instance \
    --identity-management-type <value> \
    --inbound-calls-enabled | --no-inbound-calls-enabled \
    --outbound-calls-enabled | --no-outbound-calls-enabled \
    [--instance-alias <value>] \
    [--directory-id <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-management-type` | **Yes** | string | -- | `SAML`, `CONNECT_MANAGED`, or `EXISTING_DIRECTORY` |
| `--inbound-calls-enabled` | **Yes** | boolean | -- | Enable incoming contacts |
| `--outbound-calls-enabled` | **Yes** | boolean | -- | Enable outbound calls |
| `--instance-alias` | No | string | None | Instance name (1-45 chars) |
| `--directory-id` | No | string | None | Directory ID (12 chars, for EXISTING_DIRECTORY) |
| `--client-token` | No | string | None | Idempotency token (max 500 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```

---

### 1.2 `describe-instance`

Describes an Amazon Connect instance.

**Synopsis:**
```bash
aws connect describe-instance \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output Schema:**
```json
{
    "Instance": {
        "Id": "string",
        "Arn": "string",
        "IdentityManagementType": "SAML|CONNECT_MANAGED|EXISTING_DIRECTORY",
        "InstanceAlias": "string",
        "CreatedTime": "timestamp",
        "ServiceRole": "string",
        "InstanceStatus": "CREATION_IN_PROGRESS|ACTIVE|CREATION_FAILED",
        "StatusReason": { "Message": "string" },
        "InboundCallsEnabled": "boolean",
        "OutboundCallsEnabled": "boolean",
        "InstanceAccessUrl": "string",
        "Tags": { "key": "value" },
        "ReplicationConfiguration": {
            "ReplicationStatusSummaryList": [
                { "Region": "string", "ReplicationStatus": "string", "ReplicationStatusReason": "string" }
            ],
            "SourceRegion": "string",
            "GlobalSignInEndpoint": "string"
        }
    }
}
```

---

### 1.3 `list-instances`

Lists Amazon Connect instances. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-instances \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-10) |

**Output Schema:**
```json
{
    "InstanceSummaryList": [
        {
            "Id": "string",
            "Arn": "string",
            "IdentityManagementType": "string",
            "InstanceAlias": "string",
            "CreatedTime": "timestamp",
            "ServiceRole": "string",
            "InstanceStatus": "CREATION_IN_PROGRESS|ACTIVE|CREATION_FAILED",
            "InboundCallsEnabled": "boolean",
            "OutboundCallsEnabled": "boolean",
            "InstanceAccessUrl": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `delete-instance`

Deletes an Amazon Connect instance.

**Synopsis:**
```bash
aws connect delete-instance \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output:** None

---

### 1.5 `describe-instance-attribute`

Describes a specific instance attribute.

**Synopsis:**
```bash
aws connect describe-instance-attribute \
    --instance-id <value> \
    --attribute-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--attribute-type` | **Yes** | string | -- | `INBOUND_CALLS`, `OUTBOUND_CALLS`, `CONTACTFLOW_LOGS`, `CONTACT_LENS`, `AUTO_RESOLVE_BEST_VOICES`, `USE_CUSTOM_TTS_VOICES`, `EARLY_MEDIA`, `MULTI_PARTY_CONFERENCE`, `HIGH_VOLUME_OUTBOUND`, `ENHANCED_CONTACT_MONITORING`, `ENHANCED_CHAT_MONITORING` |

**Output Schema:**
```json
{
    "Attribute": {
        "AttributeType": "string",
        "Value": "string"
    }
}
```

---

### 1.6 `list-instance-attributes`

Lists instance attributes. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-instance-attributes \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-7) |

**Output Schema:**
```json
{
    "Attributes": [
        { "AttributeType": "string", "Value": "string" }
    ],
    "NextToken": "string"
}
```

---

### 1.7 `update-instance-attribute`

Updates an instance attribute value.

**Synopsis:**
```bash
aws connect update-instance-attribute \
    --instance-id <value> \
    --attribute-type <value> \
    --value <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--attribute-type` | **Yes** | string | -- | Attribute type |
| `--value` | **Yes** | string | -- | Attribute value |

**Output:** None

---

### 1.8 `describe-instance-storage-config`

Describes instance storage configuration.

**Synopsis:**
```bash
aws connect describe-instance-storage-config \
    --instance-id <value> \
    --association-id <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--association-id` | **Yes** | string | -- | Storage config association ID |
| `--resource-type` | **Yes** | string | -- | `CHAT_TRANSCRIPTS`, `CALL_RECORDINGS`, `SCHEDULED_REPORTS`, `MEDIA_STREAMS`, `CONTACT_TRACE_RECORDS`, `AGENT_EVENTS`, `REAL_TIME_CONTACT_ANALYSIS_SEGMENTS`, `ATTACHMENTS`, `CONTACT_EVALUATIONS`, `SCREEN_RECORDINGS`, `REAL_TIME_CONTACT_ANALYSIS_CHAT_SEGMENTS`, `REAL_TIME_CONTACT_ANALYSIS_VOICE_SEGMENTS`, `EMAIL_MESSAGES` |

**Output Schema:**
```json
{
    "StorageConfig": {
        "AssociationId": "string",
        "StorageType": "S3|KINESIS_VIDEO_STREAM|KINESIS_STREAM|KINESIS_FIREHOSE",
        "S3Config": { "BucketName": "string", "BucketPrefix": "string", "EncryptionConfig": {} },
        "KinesisVideoStreamConfig": { "Prefix": "string", "RetentionPeriodHours": "integer", "EncryptionConfig": {} },
        "KinesisStreamConfig": { "StreamArn": "string" },
        "KinesisFirehoseConfig": { "FirehoseArn": "string" }
    }
}
```

---

### 1.9 `list-instance-storage-configs`

Lists instance storage configurations. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-instance-storage-configs \
    --instance-id <value> \
    --resource-type <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-type` | **Yes** | string | -- | Resource type for storage |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-10) |

**Output Schema:**
```json
{
    "StorageConfigs": [ { "AssociationId": "string", "StorageType": "string", "S3Config": {}, "KinesisVideoStreamConfig": {}, "KinesisStreamConfig": {}, "KinesisFirehoseConfig": {} } ],
    "NextToken": "string"
}
```

---

### 1.10 `associate-instance-storage-config`

Associates a storage config with an instance.

**Synopsis:**
```bash
aws connect associate-instance-storage-config \
    --instance-id <value> \
    --resource-type <value> \
    --storage-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-type` | **Yes** | string | -- | Resource type |
| `--storage-config` | **Yes** | structure | -- | Storage config object |

**Output Schema:**
```json
{
    "AssociationId": "string"
}
```

---

### 1.11 `update-instance-storage-config`

Updates an instance storage configuration.

**Synopsis:**
```bash
aws connect update-instance-storage-config \
    --instance-id <value> \
    --association-id <value> \
    --resource-type <value> \
    --storage-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--association-id` | **Yes** | string | -- | Storage config association ID |
| `--resource-type` | **Yes** | string | -- | Resource type |
| `--storage-config` | **Yes** | structure | -- | Updated storage config |

**Output:** None

---

### 1.12 `disassociate-instance-storage-config`

Removes a storage config from an instance.

**Synopsis:**
```bash
aws connect disassociate-instance-storage-config \
    --instance-id <value> \
    --association-id <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--association-id` | **Yes** | string | -- | Storage config association ID |
| `--resource-type` | **Yes** | string | -- | Resource type |

**Output:** None

---

### 1.13 `replicate-instance`

Replicates an Amazon Connect instance to another AWS region.

**Synopsis:**
```bash
aws connect replicate-instance \
    --instance-id <value> \
    --replica-region <value> \
    --replica-alias <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--replica-region` | **Yes** | string | -- | Target AWS region |
| `--replica-alias` | **Yes** | string | -- | Alias for the replica (1-45 chars) |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```
