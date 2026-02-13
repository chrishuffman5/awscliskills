# Utility

### 8.1 `check-dns-availability`

Checks if the specified CNAME is available.

**Synopsis:**
```bash
aws elasticbeanstalk check-dns-availability \
    --cname-prefix <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cname-prefix` | **Yes** | string | -- | CNAME prefix to check (4-63 chars) |

**Output Schema:**
```json
{
    "Available": "boolean",
    "FullyQualifiedCNAME": "string"
}
```

---

### 8.2 `request-environment-info`

Initiates a request to compile the specified type of information of the deployed environment. Use `retrieve-environment-info` to get the results after.

**Synopsis:**
```bash
aws elasticbeanstalk request-environment-info \
    --info-type <value> \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--info-type` | **Yes** | string | -- | Type of information: `tail` (last 100 lines of logs) or `bundle` (full log bundle) |
| `--environment-id` | No | string | -- | Environment ID |
| `--environment-name` | No | string | -- | Environment name |

**Output Schema:**
```json
{}
```

---

### 8.3 `retrieve-environment-info`

Retrieves the compiled information from a `request-environment-info` request.

**Synopsis:**
```bash
aws elasticbeanstalk retrieve-environment-info \
    --info-type <value> \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--info-type` | **Yes** | string | -- | Type of information: `tail` or `bundle` |
| `--environment-id` | No | string | -- | Environment ID |
| `--environment-name` | No | string | -- | Environment name |

**Output Schema:**
```json
{
    "EnvironmentInfo": [
        {
            "InfoType": "tail|bundle",
            "Ec2InstanceId": "string",
            "SampleTimestamp": "timestamp",
            "Message": "string"
        }
    ]
}
```

---

### 8.4 `list-tags-for-resource`

Returns the tags applied to a resource.

**Synopsis:**
```bash
aws elasticbeanstalk list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "ResourceTags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 8.5 `update-tags-for-resource`

Updates the tags of a resource. Specify both tags to add and tag keys to remove.

**Synopsis:**
```bash
aws elasticbeanstalk update-tags-for-resource \
    --resource-arn <value> \
    [--tags-to-add <value>] \
    [--tags-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags-to-add` | No | list | None | Tags to add. Shorthand: `Key=string,Value=string ...` |
| `--tags-to-remove` | No | list(string) | None | Tag keys to remove |

**Output Schema:**
```json
{}
```
