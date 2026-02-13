# Launch Configuration

### 4.1 `create-launch-configuration-template`

Creates a new launch configuration template.

**Synopsis:**
```bash
aws drs create-launch-configuration-template \
    [--copy-private-ip | --no-copy-private-ip] \
    [--copy-tags | --no-copy-tags] \
    [--export-bucket-arn <value>] \
    [--launch-disposition <value>] \
    [--launch-into-source-instance | --no-launch-into-source-instance] \
    [--licensing <value>] \
    [--post-launch-enabled | --no-post-launch-enabled] \
    [--target-instance-type-right-sizing-method <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--copy-private-ip` | No | boolean | None | Copy private IP |
| `--copy-tags` | No | boolean | None | Copy tags from source |
| `--export-bucket-arn` | No | string | None | S3 bucket ARN for export |
| `--launch-disposition` | No | string | None | `STOPPED` or `STARTED` |
| `--launch-into-source-instance` | No | boolean | None | Launch into source instance |
| `--licensing` | No | structure | None | Licensing. Shorthand: `osByol=boolean` |
| `--post-launch-enabled` | No | boolean | None | Enable post-launch actions |
| `--target-instance-type-right-sizing-method` | No | string | None | `NONE`, `BASIC`, `IN_AWS` |
| `--tags` | No | map | None | Tags for the template |

**Output Schema:**
```json
{
    "launchConfigurationTemplate": {
        "launchConfigurationTemplateID": "string",
        "arn": "string",
        "copyPrivateIp": "boolean",
        "copyTags": "boolean",
        "exportBucketArn": "string",
        "launchDisposition": "STOPPED|STARTED",
        "launchIntoSourceInstance": "boolean",
        "licensing": {
            "osByol": "boolean"
        },
        "postLaunchEnabled": "boolean",
        "targetInstanceTypeRightSizingMethod": "NONE|BASIC|IN_AWS",
        "tags": {}
    }
}
```

---

### 4.2 `delete-launch-configuration-template`

Deletes a single launch configuration template.

**Synopsis:**
```bash
aws drs delete-launch-configuration-template \
    --launch-configuration-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-template-id` | **Yes** | string | -- | Template ID |

**Output Schema:**
```json
{}
```

---

### 4.3 `describe-launch-configuration-templates`

Lists all launch configuration templates, filtered by IDs. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-launch-configuration-templates \
    [--launch-configuration-template-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-template-ids` | No | list(string) | None | Template IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "items": [
        {
            "launchConfigurationTemplateID": "string",
            "arn": "string",
            "copyPrivateIp": "boolean",
            "copyTags": "boolean",
            "exportBucketArn": "string",
            "launchDisposition": "STOPPED|STARTED",
            "launchIntoSourceInstance": "boolean",
            "licensing": {
                "osByol": "boolean"
            },
            "postLaunchEnabled": "boolean",
            "targetInstanceTypeRightSizingMethod": "NONE|BASIC|IN_AWS",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `update-launch-configuration-template`

Updates an existing launch configuration template.

**Synopsis:**
```bash
aws drs update-launch-configuration-template \
    --launch-configuration-template-id <value> \
    [--copy-private-ip | --no-copy-private-ip] \
    [--copy-tags | --no-copy-tags] \
    [--export-bucket-arn <value>] \
    [--launch-disposition <value>] \
    [--launch-into-source-instance | --no-launch-into-source-instance] \
    [--licensing <value>] \
    [--post-launch-enabled | --no-post-launch-enabled] \
    [--target-instance-type-right-sizing-method <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-template-id` | **Yes** | string | -- | Template ID |
| `--copy-private-ip` | No | boolean | None | Copy private IP |
| `--copy-tags` | No | boolean | None | Copy tags |
| `--export-bucket-arn` | No | string | None | S3 bucket ARN |
| `--launch-disposition` | No | string | None | `STOPPED` or `STARTED` |
| `--launch-into-source-instance` | No | boolean | None | Launch into source |
| `--licensing` | No | structure | None | Licensing |
| `--post-launch-enabled` | No | boolean | None | Post-launch actions |
| `--target-instance-type-right-sizing-method` | No | string | None | Right-sizing method |

**Output Schema:** Same as `create-launch-configuration-template`.

---

### 4.5 `get-launch-configuration`

Gets the launch configuration for a specific source server.

**Synopsis:**
```bash
aws drs get-launch-configuration \
    --source-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |

**Output Schema:**
```json
{
    "sourceServerID": "string",
    "name": "string",
    "ec2LaunchTemplateID": "string",
    "launchDisposition": "STOPPED|STARTED",
    "targetInstanceTypeRightSizingMethod": "NONE|BASIC|IN_AWS",
    "copyPrivateIp": "boolean",
    "copyTags": "boolean",
    "licensing": {
        "osByol": "boolean"
    },
    "postLaunchEnabled": "boolean",
    "launchIntoInstanceProperties": {
        "launchIntoEC2InstanceID": "string"
    }
}
```

---

### 4.6 `update-launch-configuration`

Updates the launch configuration for a specific source server.

**Synopsis:**
```bash
aws drs update-launch-configuration \
    --source-server-id <value> \
    [--name <value>] \
    [--launch-disposition <value>] \
    [--target-instance-type-right-sizing-method <value>] \
    [--copy-private-ip | --no-copy-private-ip] \
    [--copy-tags | --no-copy-tags] \
    [--licensing <value>] \
    [--post-launch-enabled | --no-post-launch-enabled] \
    [--launch-into-instance-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--name` | No | string | None | Configuration name |
| `--launch-disposition` | No | string | None | `STOPPED` or `STARTED` |
| `--target-instance-type-right-sizing-method` | No | string | None | Right-sizing method |
| `--copy-private-ip` | No | boolean | None | Copy private IP |
| `--copy-tags` | No | boolean | None | Copy tags |
| `--licensing` | No | structure | None | Licensing |
| `--post-launch-enabled` | No | boolean | None | Post-launch actions |
| `--launch-into-instance-properties` | No | structure | None | Launch into existing instance |

**Output Schema:** Same as `get-launch-configuration`.

---

### 4.7 `put-launch-action`

Puts a launch action for a source server.

**Synopsis:**
```bash
aws drs put-launch-action \
    --resource-id <value> \
    --action-code <value> \
    --action-id <value> \
    --action-version <value> \
    --active | --no-active \
    --category <value> \
    --description <value> \
    --name <value> \
    --order <value> \
    [--optional | --no-optional] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Source server ID |
| `--action-code` | **Yes** | string | -- | Launch action code |
| `--action-id` | **Yes** | string | -- | Launch action ID |
| `--action-version` | **Yes** | string | -- | Launch action version |
| `--active` | **Yes** | boolean | -- | Whether action is active |
| `--category` | **Yes** | string | -- | `MONITORING`, `VALIDATION`, `CONFIGURATION`, `SECURITY`, `OTHER` |
| `--description` | **Yes** | string | -- | Description |
| `--name` | **Yes** | string | -- | Action name |
| `--order` | **Yes** | integer | -- | Order of execution |
| `--optional` | No | boolean | None | Whether action is optional |
| `--parameters` | No | map | None | Action parameters |

**Output Schema:**
```json
{
    "resourceId": "string",
    "actionCode": "string",
    "actionId": "string",
    "actionVersion": "string",
    "active": "boolean",
    "category": "MONITORING|VALIDATION|CONFIGURATION|SECURITY|OTHER",
    "description": "string",
    "name": "string",
    "order": "integer",
    "optional": "boolean",
    "parameters": {},
    "type": "SSM_AUTOMATION|SSM_COMMAND"
}
```

---

### 4.8 `delete-launch-action`

Deletes a launch action for a source server.

**Synopsis:**
```bash
aws drs delete-launch-action \
    --resource-id <value> \
    --action-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Source server ID |
| `--action-id` | **Yes** | string | -- | Launch action ID |

**Output Schema:**
```json
{}
```

---

### 4.9 `list-launch-actions`

Lists launch actions for a source server. **Paginated operation.**

**Synopsis:**
```bash
aws drs list-launch-actions \
    --resource-id <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Source server ID |
| `--filters` | No | structure | None | Filters. Structure: `actionIds=string,string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "items": [
        {
            "resourceId": "string",
            "actionCode": "string",
            "actionId": "string",
            "actionVersion": "string",
            "active": "boolean",
            "category": "MONITORING|VALIDATION|CONFIGURATION|SECURITY|OTHER",
            "description": "string",
            "name": "string",
            "order": "integer",
            "optional": "boolean",
            "parameters": {},
            "type": "SSM_AUTOMATION|SSM_COMMAND"
        }
    ],
    "nextToken": "string"
}
```
