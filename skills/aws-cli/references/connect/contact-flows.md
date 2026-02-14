# Contact Flows

### 2.1 `create-contact-flow`

Creates a contact flow for the specified instance.

**Synopsis:**
```bash
aws connect create-contact-flow \
    --instance-id <value> \
    --name <value> \
    --type <value> \
    --content <value> \
    [--description <value>] \
    [--status <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Flow name (min 1 char) |
| `--type` | **Yes** | string | -- | `CONTACT_FLOW`, `CUSTOMER_QUEUE`, `CUSTOMER_HOLD`, `CUSTOMER_WHISPER`, `AGENT_HOLD`, `AGENT_WHISPER`, `OUTBOUND_WHISPER`, `AGENT_TRANSFER`, `QUEUE_TRANSFER`, `CAMPAIGN` |
| `--content` | **Yes** | string | -- | Flow content JSON (max 256000 chars) |
| `--description` | No | string | None | Flow description |
| `--status` | No | string | None | `PUBLISHED` or `SAVED` |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "ContactFlowId": "string",
    "ContactFlowArn": "string",
    "FlowContentSha256": "string"
}
```

---

### 2.2 `describe-contact-flow`

Describes a contact flow.

**Synopsis:**
```bash
aws connect describe-contact-flow \
    --instance-id <value> \
    --contact-flow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |

**Output Schema:**
```json
{
    "ContactFlow": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "Type": "string",
        "State": "ACTIVE|ARCHIVED",
        "Status": "PUBLISHED|SAVED",
        "Description": "string",
        "Content": "string",
        "Tags": { "key": "value" },
        "IsDefault": "boolean",
        "FlowContentSha256": "string",
        "Version": "long",
        "VersionDescription": "string",
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 2.3 `list-contact-flows`

Lists contact flows. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-contact-flows \
    --instance-id <value> \
    [--contact-flow-types <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-types` | No | list | None | Filter by flow types |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "ContactFlowSummaryList": [
        { "Id": "string", "Arn": "string", "Name": "string", "ContactFlowType": "string", "ContactFlowState": "string", "ContactFlowStatus": "string" }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-contact-flow-content`

Updates the content of a contact flow.

**Synopsis:**
```bash
aws connect update-contact-flow-content \
    --instance-id <value> \
    --contact-flow-id <value> \
    --content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--content` | **Yes** | string | -- | Updated flow content JSON |

**Output Schema:**
```json
{
    "FlowContentSha256": "string"
}
```

---

### 2.5 `update-contact-flow-metadata`

Updates the metadata of a contact flow.

**Synopsis:**
```bash
aws connect update-contact-flow-metadata \
    --instance-id <value> \
    --contact-flow-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--contact-flow-state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--contact-flow-state` | No | string | None | `ACTIVE` or `ARCHIVED` |

**Output:** None

---

### 2.6 `update-contact-flow-name`

Updates the name and description of a contact flow.

**Synopsis:**
```bash
aws connect update-contact-flow-name \
    --instance-id <value> \
    --contact-flow-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

**Output:** None

---

### 2.7 `delete-contact-flow`

Deletes a contact flow.

**Synopsis:**
```bash
aws connect delete-contact-flow \
    --instance-id <value> \
    --contact-flow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |

**Output:** None

---

### 2.8 `create-contact-flow-version`

Publishes a new version of a contact flow.

**Synopsis:**
```bash
aws connect create-contact-flow-version \
    --instance-id <value> \
    --contact-flow-id <value> \
    [--description <value>] \
    [--flow-content-sha256 <value>] \
    [--contact-flow-version <value>] \
    [--last-modified-time <value>] \
    [--last-modified-region <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--description` | No | string | None | Version description |
| `--flow-content-sha256` | No | string | None | SHA256 checksum for conflict detection |
| `--contact-flow-version` | No | long | None | Specific version number |
| `--last-modified-time` | No | timestamp | None | Last modified time for conflict detection |
| `--last-modified-region` | No | string | None | Last modified region |

**Output Schema:**
```json
{
    "ContactFlowArn": "string",
    "Version": "long"
}
```

---

### 2.9 `list-contact-flow-versions`

Lists versions of a contact flow. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-contact-flow-versions \
    --instance-id <value> \
    --contact-flow-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "ContactFlowVersionSummaryList": [
        { "Arn": "string", "Version": "long", "VersionDescription": "string" }
    ],
    "NextToken": "string"
}
```

---

### 2.10 `delete-contact-flow-version`

Deletes a specific version of a contact flow.

**Synopsis:**
```bash
aws connect delete-contact-flow-version \
    --instance-id <value> \
    --contact-flow-id <value> \
    --contact-flow-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--contact-flow-version` | **Yes** | long | -- | Version to delete |

**Output:** None

---

### 2.11 `create-contact-flow-module`

Creates a contact flow module.

**Synopsis:**
```bash
aws connect create-contact-flow-module \
    --instance-id <value> \
    --name <value> \
    --content <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Module name (1-127 chars) |
| `--content` | **Yes** | string | -- | Module content JSON |
| `--description` | No | string | None | Module description |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```

---

### 2.12 `describe-contact-flow-module`

Describes a contact flow module.

**Synopsis:**
```bash
aws connect describe-contact-flow-module \
    --instance-id <value> \
    --contact-flow-module-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-module-id` | **Yes** | string | -- | Module ID |

**Output Schema:**
```json
{
    "ContactFlowModule": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "Content": "string",
        "Description": "string",
        "State": "ACTIVE|ARCHIVED",
        "Status": "PUBLISHED|SAVED",
        "Tags": { "key": "value" }
    }
}
```

---

### 2.13 `list-contact-flow-modules`

Lists contact flow modules. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-contact-flow-modules \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--contact-flow-module-state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |
| `--contact-flow-module-state` | No | string | None | `ACTIVE` or `ARCHIVED` |

**Output Schema:**
```json
{
    "ContactFlowModulesSummaryList": [
        { "Id": "string", "Arn": "string", "Name": "string", "State": "string" }
    ],
    "NextToken": "string"
}
```

---

### 2.14 `update-contact-flow-module-content`

Updates contact flow module content.

**Synopsis:**
```bash
aws connect update-contact-flow-module-content \
    --instance-id <value> \
    --contact-flow-module-id <value> \
    --content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-module-id` | **Yes** | string | -- | Module ID |
| `--content` | **Yes** | string | -- | Updated module content JSON |

**Output:** None

---

### 2.15 `update-contact-flow-module-metadata`

Updates contact flow module metadata.

**Synopsis:**
```bash
aws connect update-contact-flow-module-metadata \
    --instance-id <value> \
    --contact-flow-module-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-module-id` | **Yes** | string | -- | Module ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--state` | No | string | None | `ACTIVE` or `ARCHIVED` |

**Output:** None

---

### 2.16 `delete-contact-flow-module`

Deletes a contact flow module.

**Synopsis:**
```bash
aws connect delete-contact-flow-module \
    --instance-id <value> \
    --contact-flow-module-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-module-id` | **Yes** | string | -- | Module ID |

**Output:** None

---

### 2.17 `create-contact-flow-module-alias`

Creates an alias for a contact flow module.

**Synopsis:**
```bash
aws connect create-contact-flow-module-alias \
    --instance-id <value> \
    --contact-flow-module-id <value> \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-module-id` | **Yes** | string | -- | Module ID |
| `--name` | **Yes** | string | -- | Alias name |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "ContactFlowModuleAlias": {
        "Arn": "string",
        "Id": "string",
        "Name": "string"
    }
}
```

---

### 2.18-2.22 Module Alias & Version Commands

`describe-contact-flow-module-alias`, `list-contact-flow-module-aliases`, `update-contact-flow-module-alias`, `delete-contact-flow-module-alias`, `create-contact-flow-module-version`, `list-contact-flow-module-versions`, `delete-contact-flow-module-version` follow the same pattern as their contact flow counterparts with `--instance-id`, `--contact-flow-module-id`, and alias/version-specific parameters.

---

### 2.23 `search-contact-flows`

Searches contact flows. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-contact-flows \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--search-filter <value>] \
    [--search-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-filter` | No | structure | None | Tag filter conditions |
| `--search-criteria` | No | structure | None | Search criteria with string/type conditions |

**Output Schema:**
```json
{
    "ContactFlows": [ { "Arn": "string", "Id": "string", "Name": "string", "Type": "string", "State": "string", "Status": "string", "Description": "string", "Content": "string", "Tags": {} } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```

---

### 2.24 `search-contact-flow-modules`

Searches contact flow modules. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-contact-flow-modules \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--search-filter <value>] \
    [--search-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-filter` | No | structure | None | Tag filter conditions |
| `--search-criteria` | No | structure | None | Search criteria |

**Output Schema:**
```json
{
    "ContactFlowModules": [ { "Arn": "string", "Id": "string", "Name": "string", "Content": "string", "Description": "string", "State": "string", "Status": "string", "Tags": {} } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```
