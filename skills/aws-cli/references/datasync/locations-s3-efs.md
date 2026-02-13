# Locations (S3 & EFS)

### 3.1 `create-location-s3`

Creates a transfer location for an Amazon S3 bucket.

**Synopsis:**
```bash
aws datasync create-location-s3 \
    --s3-bucket-arn <value> \
    --s3-config <value> \
    [--subdirectory <value>] \
    [--s3-storage-class <value>] \
    [--agent-arns <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-bucket-arn` | **Yes** | string | -- | ARN of the S3 bucket |
| `--s3-config` | **Yes** | structure | -- | IAM role config for S3 access |
| `--subdirectory` | No | string | None | Prefix in the S3 bucket |
| `--s3-storage-class` | No | string | None | Storage class for transferred objects |
| `--agent-arns` | No | list(string) | None | Agent ARNs (for on-premises S3-compatible storage) |
| `--tags` | No | list | None | Tags (max 50) |

**S3 Config Structure (shorthand):**
```
BucketAccessRoleArn=string
```

**S3 Storage Class Values:**
`STANDARD` | `STANDARD_IA` | `ONEZONE_IA` | `INTELLIGENT_TIERING` | `GLACIER` | `GLACIER_INSTANT_RETRIEVAL` | `DEEP_ARCHIVE` | `OUTPOSTS`

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 3.2 `describe-location-s3`

Gets details about an S3 location.

**Synopsis:**
```bash
aws datasync describe-location-s3 \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the S3 location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "S3StorageClass": "STANDARD|STANDARD_IA|ONEZONE_IA|INTELLIGENT_TIERING|GLACIER|GLACIER_INSTANT_RETRIEVAL|DEEP_ARCHIVE|OUTPOSTS",
    "S3Config": {
        "BucketAccessRoleArn": "string"
    },
    "AgentArns": ["string"],
    "CreationTime": "timestamp"
}
```

---

### 3.3 `update-location-s3`

Updates an S3 location configuration.

**Synopsis:**
```bash
aws datasync update-location-s3 \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--s3-storage-class <value>] \
    [--s3-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the S3 location |
| `--subdirectory` | No | string | None | New S3 prefix |
| `--s3-storage-class` | No | string | None | New storage class |
| `--s3-config` | No | structure | None | New IAM role config |

**Output:** None on success.

---

### 3.4 `create-location-efs`

Creates a transfer location for an Amazon EFS file system.

**Synopsis:**
```bash
aws datasync create-location-efs \
    --efs-filesystem-arn <value> \
    --ec2-config <value> \
    [--subdirectory <value>] \
    [--tags <value>] \
    [--access-point-arn <value>] \
    [--file-system-access-role-arn <value>] \
    [--in-transit-encryption <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--efs-filesystem-arn` | **Yes** | string | -- | ARN of the EFS file system |
| `--ec2-config` | **Yes** | structure | -- | Subnet and security group config |
| `--subdirectory` | No | string | `/` | Mount path in the EFS file system |
| `--tags` | No | list | None | Tags (max 50) |
| `--access-point-arn` | No | string | None | EFS access point ARN |
| `--file-system-access-role-arn` | No | string | None | IAM role for EFS access |
| `--in-transit-encryption` | No | string | None | `NONE` or `TLS1_2` |

**EC2 Config Structure (shorthand):**
```
SubnetArn=string,SecurityGroupArns=string,string
```

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 3.5 `describe-location-efs`

Gets details about an EFS location.

**Synopsis:**
```bash
aws datasync describe-location-efs \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the EFS location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "Ec2Config": {
        "SubnetArn": "string",
        "SecurityGroupArns": ["string"]
    },
    "CreationTime": "timestamp",
    "AccessPointArn": "string",
    "FileSystemAccessRoleArn": "string",
    "InTransitEncryption": "NONE|TLS1_2"
}
```

---

### 3.6 `update-location-efs`

Updates an EFS location configuration.

**Synopsis:**
```bash
aws datasync update-location-efs \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--access-point-arn <value>] \
    [--file-system-access-role-arn <value>] \
    [--in-transit-encryption <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the EFS location |
| `--subdirectory` | No | string | None | New mount path |
| `--access-point-arn` | No | string | None | New access point ARN |
| `--file-system-access-role-arn` | No | string | None | New IAM role ARN |
| `--in-transit-encryption` | No | string | None | `NONE` or `TLS1_2` |

**Output:** None on success.
