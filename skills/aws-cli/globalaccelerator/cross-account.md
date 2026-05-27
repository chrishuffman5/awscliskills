# Cross-Account Attachments

Commands for managing cross-account resource sharing in AWS Global Accelerator.

### 5.1 `create-cross-account-attachment`

Creates a cross-account attachment, allowing another account's resources to be used as endpoints.

**Synopsis:**
```bash
aws globalaccelerator create-cross-account-attachment \
    --name <value> \
    [--principals <value>] \
    [--resources <value>] \
    [--idempotency-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the attachment (max 64 chars) |
| `--principals` | No | list(string) | None | AWS account IDs or accelerator ARNs to grant access |
| `--resources` | No | list | None | Resources to share |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags |

**Resource Structure (JSON):**
```json
[
    {
        "EndpointId": "string",
        "Cidr": "string",
        "Region": "string"
    }
]
```

**Output Schema:**
```json
{
    "CrossAccountAttachment": {
        "AttachmentArn": "string",
        "Name": "string",
        "Principals": ["string"],
        "Resources": [
            {
                "EndpointId": "string",
                "Cidr": "string",
                "Region": "string"
            }
        ],
        "LastModifiedTime": "timestamp",
        "CreatedTime": "timestamp"
    }
}
```

---

### 5.2 `delete-cross-account-attachment`

Deletes a cross-account attachment.

**Synopsis:**
```bash
aws globalaccelerator delete-cross-account-attachment \
    --attachment-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-arn` | **Yes** | string | -- | ARN of the attachment to delete |

**Output:** None on success.

---

### 5.3 `describe-cross-account-attachment`

Gets details about a cross-account attachment.

**Synopsis:**
```bash
aws globalaccelerator describe-cross-account-attachment \
    --attachment-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-arn` | **Yes** | string | -- | ARN of the attachment |

**Output Schema:** Same as `create-cross-account-attachment`.

---

### 5.4 `list-cross-account-attachments`

Lists all cross-account attachments. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-cross-account-attachments \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CrossAccountAttachments": [
        {
            "AttachmentArn": "string",
            "Name": "string",
            "Principals": ["string"],
            "Resources": [],
            "LastModifiedTime": "timestamp",
            "CreatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-cross-account-attachment`

Updates a cross-account attachment (principals and/or resources).

**Synopsis:**
```bash
aws globalaccelerator update-cross-account-attachment \
    --attachment-arn <value> \
    [--name <value>] \
    [--add-principals <value>] \
    [--remove-principals <value>] \
    [--add-resources <value>] \
    [--remove-resources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-arn` | **Yes** | string | -- | ARN of the attachment |
| `--name` | No | string | None | New name |
| `--add-principals` | No | list(string) | None | Principals to add |
| `--remove-principals` | No | list(string) | None | Principals to remove |
| `--add-resources` | No | list | None | Resources to add |
| `--remove-resources` | No | list | None | Resources to remove |

**Output Schema:** Same as `create-cross-account-attachment`.

---

### 5.6 `list-cross-account-resource-accounts`

Lists AWS accounts that have cross-account resources in this account. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-cross-account-resource-accounts \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceOwnerAwsAccountIds": ["string"],
    "NextToken": "string"
}
```

---

### 5.7 `list-cross-account-resources`

Lists cross-account resources available from a specific account. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-cross-account-resources \
    --resource-owner-aws-account-id <value> \
    [--accelerator-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-owner-aws-account-id` | **Yes** | string | -- | AWS account ID of the resource owner |
| `--accelerator-arn` | No | string | None | Filter by accelerator ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CrossAccountResources": [
        {
            "EndpointId": "string",
            "Cidr": "string",
            "AttachmentArn": "string"
        }
    ],
    "NextToken": "string"
}
```
