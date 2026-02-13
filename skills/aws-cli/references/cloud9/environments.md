# Environments

### 1.1 `create-environment-ec2`

Creates an AWS Cloud9 development environment backed by an Amazon EC2 instance.

**Synopsis:**
```bash
aws cloud9 create-environment-ec2 \
    --name <value> \
    --instance-type <value> \
    --image-id <value> \
    [--description <value>] \
    [--client-request-token <value>] \
    [--subnet-id <value>] \
    [--automatic-stop-time-minutes <value>] \
    [--owner-arn <value>] \
    [--tags <value>] \
    [--connection-type <value>] \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name of the environment (1-60 chars) |
| `--instance-type` | **Yes** | string | -- | EC2 instance type (e.g., `t2.micro`, `t3.small`, `m5.large`) |
| `--image-id` | **Yes** | string | -- | AMI image identifier: `amazonlinux-2-x86_64`, `amazonlinux-2023-x86_64`, `ubuntu-18.04-x86_64`, `ubuntu-22.04-x86_64`, `resolve:ssm:/aws/service/cloud9/amis/amazonlinux-2-x86_64` |
| `--description` | No | string | None | Description of the environment (max 200 chars) |
| `--client-request-token` | No | string | None | Idempotency token |
| `--subnet-id` | No | string | None | Subnet ID for the instance. If not specified, uses default VPC |
| `--automatic-stop-time-minutes` | No | integer | 30 | Minutes of inactivity before auto-stopping (0-20160). 0 means no auto-stop |
| `--owner-arn` | No | string | caller | ARN of the environment owner |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--connection-type` | No | string | `CONNECT_SSM` | Connection type: `CONNECT_SSH`, `CONNECT_SSM` |
| `--dry-run` | No | boolean | false | Validate without creating the environment |

**Output Schema:**
```json
{
    "environmentId": "string"
}
```

---

### 1.2 `delete-environment`

Deletes an AWS Cloud9 development environment. If an Amazon EC2 instance is connected, it is also terminated.

**Synopsis:**
```bash
aws cloud9 delete-environment \
    --environment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | The ID of the environment to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-environments`

Gets information about one or more AWS Cloud9 development environments.

**Synopsis:**
```bash
aws cloud9 describe-environments \
    --environment-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-ids` | **Yes** | list(string) | -- | One or more environment IDs (max 25) |

**Output Schema:**
```json
{
    "environments": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "type": "ssh|ec2",
            "connectionType": "CONNECT_SSH|CONNECT_SSM",
            "arn": "string",
            "ownerArn": "string",
            "lifecycle": {
                "status": "CREATING|CREATED|CREATE_FAILED|DELETING|DELETE_FAILED",
                "reason": "string",
                "failureResource": "string"
            },
            "managedCredentialsStatus": "ENABLED_ON_CREATE|ENABLED_BY_OWNER|DISABLED_BY_DEFAULT|DISABLED_BY_OWNER|DISABLED_BY_COLLABORATOR|PENDING_REMOVAL_BY_COLLABORATOR|PENDING_START_REMOVAL_BY_COLLABORATOR|PENDING_REMOVAL_BY_OWNER|FAILED_REMOVAL_BY_COLLABORATOR|FAILED_REMOVAL_BY_OWNER",
            "managedCredentialsAction": "ENABLE|DISABLE"
        }
    ]
}
```

---

### 1.4 `list-environments`

Gets a list of AWS Cloud9 development environment identifiers. **Paginated operation.**

**Synopsis:**
```bash
aws cloud9 list-environments \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 25) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "environmentIds": ["string"],
    "nextToken": "string"
}
```

---

### 1.5 `update-environment`

Changes the settings of an existing AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 update-environment \
    --environment-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--managed-credentials-action <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | The ID of the environment to update |
| `--name` | No | string | None | New name (1-60 chars) |
| `--description` | No | string | None | New description (max 200 chars) |
| `--managed-credentials-action` | No | string | None | Managed credentials action: `ENABLE`, `DISABLE` |

**Output Schema:**
```json
{}
```

---

### 1.6 `describe-environment-status`

Gets status information for an AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 describe-environment-status \
    --environment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | The ID of the environment |

**Output Schema:**
```json
{
    "status": "error|creating|connecting|ready|stopping|stopped|deleting",
    "message": "string"
}
```
