# Projects

### 1.1 `create-project`

Creates a new Device Farm project.

**Synopsis:**
```bash
aws devicefarm create-project \
    --name <value> \
    [--default-job-timeout-minutes <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the project |
| `--default-job-timeout-minutes` | No | integer | 150 | Default timeout in minutes for jobs in this project |
| `--vpc-config` | No | structure | None | VPC configuration. JSON: `{"securityGroupIds":["string"],"subnetIds":["string"],"vpcId":"string"}` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "project": {
        "arn": "string",
        "name": "string",
        "defaultJobTimeoutMinutes": "integer",
        "created": "timestamp",
        "vpcConfig": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"],
            "vpcId": "string"
        }
    }
}
```

---

### 1.2 `delete-project`

Deletes a Device Farm project and all its associated runs, jobs, suites, tests, uploads, and artifacts.

**Synopsis:**
```bash
aws devicefarm delete-project \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `get-project`

Gets information about a project.

**Synopsis:**
```bash
aws devicefarm get-project \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project |

**Output Schema:**
```json
{
    "project": {
        "arn": "string",
        "name": "string",
        "defaultJobTimeoutMinutes": "integer",
        "created": "timestamp",
        "vpcConfig": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"],
            "vpcId": "string"
        }
    }
}
```

---

### 1.4 `list-projects`

Gets information about projects. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-projects \
    [--arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | No | string | None | ARN filter (not commonly used) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "projects": [
        {
            "arn": "string",
            "name": "string",
            "defaultJobTimeoutMinutes": "integer",
            "created": "timestamp",
            "vpcConfig": {
                "securityGroupIds": ["string"],
                "subnetIds": ["string"],
                "vpcId": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-project`

Modifies a Device Farm project.

**Synopsis:**
```bash
aws devicefarm update-project \
    --arn <value> \
    [--name <value>] \
    [--default-job-timeout-minutes <value>] \
    [--vpc-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project to update |
| `--name` | No | string | None | Updated project name |
| `--default-job-timeout-minutes` | No | integer | None | Updated default timeout |
| `--vpc-config` | No | structure | None | Updated VPC configuration |

**Output Schema:**
```json
{
    "project": {
        "arn": "string",
        "name": "string",
        "defaultJobTimeoutMinutes": "integer",
        "created": "timestamp",
        "vpcConfig": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"],
            "vpcId": "string"
        }
    }
}
```

---

### 1.6 `get-account-settings`

Returns the number of unmetered iOS or Android devices purchased, and the number of available device minutes.

**Synopsis:**
```bash
aws devicefarm get-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| -- | -- | -- | -- | No required parameters |

**Output Schema:**
```json
{
    "accountSettings": {
        "awsAccountNumber": "string",
        "unmeteredDevices": {
            "ANDROID": "integer",
            "IOS": "integer"
        },
        "unmeteredRemoteAccessDevices": {
            "ANDROID": "integer",
            "IOS": "integer"
        },
        "maxJobTimeoutMinutes": "integer",
        "trialMinutes": {
            "total": "double",
            "remaining": "double"
        },
        "maxSlots": {
            "string": "integer"
        },
        "defaultJobTimeoutMinutes": "integer",
        "skipAppResign": "boolean"
    }
}
```
