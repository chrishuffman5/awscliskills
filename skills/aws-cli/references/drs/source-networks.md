# Source Networks

### 6.1 `create-source-network`

Creates a new source network to replicate to DRS.

**Synopsis:**
```bash
aws drs create-source-network \
    --origin-account-id <value> \
    --origin-region <value> \
    --vpc-id <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origin-account-id` | **Yes** | string | -- | Origin AWS account ID |
| `--origin-region` | **Yes** | string | -- | Origin AWS region |
| `--vpc-id` | **Yes** | string | -- | VPC ID to replicate |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "sourceNetworkID": "string"
}
```

---

### 6.2 `delete-source-network`

Deletes a source network.

**Synopsis:**
```bash
aws drs delete-source-network \
    --source-network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-network-id` | **Yes** | string | -- | Source network ID |

**Output Schema:**
```json
{}
```

---

### 6.3 `describe-source-networks`

Lists all source networks or those that match given filters. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-source-networks \
    --filters <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | **Yes** | structure | -- | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Filters Structure:**
```json
{
    "sourceNetworkIDs": ["string"],
    "originAccountID": "string",
    "originRegion": "string"
}
```

**Output Schema:**
```json
{
    "items": [
        {
            "sourceNetworkID": "string",
            "sourceVpcID": "string",
            "arn": "string",
            "sourceAccountID": "string",
            "sourceRegion": "string",
            "cfnStackName": "string",
            "replicationStatus": "STOPPED|IN_PROGRESS|PROTECTED|ERROR",
            "replicationStatusDetails": "string",
            "lastRecoveryResult": "NOT_STARTED|IN_PROGRESS|SUCCESS|FAIL",
            "launchedVpcID": "string",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 6.4 `start-source-network-recovery`

Starts recovery of the specified source networks.

**Synopsis:**
```bash
aws drs start-source-network-recovery \
    --source-networks <value> \
    [--deploy-as-new | --no-deploy-as-new] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-networks` | **Yes** | list | -- | Source networks to recover. Shorthand: `sourceNetworkID=string,cfnStackName=string ...` |
| `--deploy-as-new` | No | boolean | false | Deploy as a new network |
| `--tags` | No | map | None | Tags for the job |

**Output Schema:**
```json
{
    "job": {
        "jobID": "string",
        "arn": "string",
        "type": "LAUNCH",
        "initiatedBy": "CREATE_NETWORK_RECOVERY",
        "creationDateTime": "string",
        "endDateTime": "string",
        "status": "PENDING|STARTED|COMPLETED",
        "participatingServers": [],
        "participatingResources": [
            {
                "participatingResourceID": {
                    "sourceNetworkID": "string"
                },
                "launchStatus": "PENDING|IN_PROGRESS|LAUNCHED|FAILED|TERMINATED"
            }
        ],
        "tags": {}
    }
}
```

---

### 6.5 `start-source-network-replication`

Starts replication for a source network.

**Synopsis:**
```bash
aws drs start-source-network-replication \
    --source-network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-network-id` | **Yes** | string | -- | Source network ID |

**Output Schema:**
```json
{
    "sourceNetwork": {
        "sourceNetworkID": "string",
        "sourceVpcID": "string",
        "arn": "string",
        "sourceAccountID": "string",
        "sourceRegion": "string",
        "cfnStackName": "string",
        "replicationStatus": "STOPPED|IN_PROGRESS|PROTECTED|ERROR",
        "replicationStatusDetails": "string",
        "lastRecoveryResult": "NOT_STARTED|IN_PROGRESS|SUCCESS|FAIL",
        "launchedVpcID": "string",
        "tags": {}
    }
}
```

---

### 6.6 `stop-source-network-replication`

Stops replication for a source network.

**Synopsis:**
```bash
aws drs stop-source-network-replication \
    --source-network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-network-id` | **Yes** | string | -- | Source network ID |

**Output Schema:** Same as `start-source-network-replication`.

---

### 6.7 `associate-source-network-stack`

Associate a CloudFormation stack with a source network.

**Synopsis:**
```bash
aws drs associate-source-network-stack \
    --source-network-id <value> \
    --cfn-stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-network-id` | **Yes** | string | -- | Source network ID |
| `--cfn-stack-name` | **Yes** | string | -- | CloudFormation stack name or ARN |

**Output Schema:**
```json
{
    "job": {
        "jobID": "string",
        "arn": "string",
        "type": "LAUNCH",
        "initiatedBy": "ASSOCIATE_NETWORK_RECOVERY",
        "creationDateTime": "string",
        "endDateTime": "string",
        "status": "PENDING|STARTED|COMPLETED",
        "participatingServers": [],
        "participatingResources": [],
        "tags": {}
    }
}
```

---

### 6.8 `export-source-network-cfn-template`

Export the CloudFormation template for a source network that was previously recovered.

**Synopsis:**
```bash
aws drs export-source-network-cfn-template \
    --source-network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-network-id` | **Yes** | string | -- | Source network ID |

**Output Schema:**
```json
{
    "s3DestinationUrl": "string"
}
```
