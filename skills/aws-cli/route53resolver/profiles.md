# Profiles

> These commands use the `aws route53profiles` service prefix.

### 7.1 `create-profile`

Creates a Route 53 Profile for sharing DNS configurations across VPCs and accounts.

**Synopsis:**
```bash
aws route53profiles create-profile \
    --name <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Profile name (max 64 chars) |
| `--client-token` | No | string | None | Idempotency token (max 255 chars) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Profile": {
        "Arn": "string",
        "ClientToken": "string",
        "CreationTime": "timestamp",
        "Id": "string",
        "ModificationTime": "timestamp",
        "Name": "string",
        "OwnerId": "string",
        "ShareStatus": "NOT_SHARED|SHARED_WITH_ME|SHARED_BY_ME",
        "Status": "COMPLETE|DELETING|UPDATING|CREATING|DELETED|FAILED",
        "StatusMessage": "string"
    }
}
```

---

### 7.2 `delete-profile`

Deletes a Route 53 Profile. All VPC associations and resource associations must be removed first.

**Synopsis:**
```bash
aws route53profiles delete-profile \
    --profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | The profile ID (max 64 chars) |

**Output Schema:**
Same as `create-profile` output.

---

### 7.3 `get-profile`

Gets details of a Route 53 Profile.

**Synopsis:**
```bash
aws route53profiles get-profile \
    --profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | The profile ID (max 64 chars) |

**Output Schema:**
Same as `create-profile` output.

---

### 7.4 `list-profiles`

Lists all Route 53 Profiles. **Paginated.**

**Synopsis:**
```bash
aws route53profiles list-profiles \
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
    "ProfileSummaries": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "ShareStatus": "NOT_SHARED|SHARED_WITH_ME|SHARED_BY_ME"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `associate-profile`

Associates a Route 53 Profile with a VPC. A VPC can have only one profile associated.

**Synopsis:**
```bash
aws route53profiles associate-profile \
    --name <value> \
    --profile-id <value> \
    --resource-id <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Association name (max 64 chars) |
| `--profile-id` | **Yes** | string | -- | The profile ID (max 64 chars) |
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "ProfileAssociation": {
        "CreationTime": "timestamp",
        "Id": "string",
        "ModificationTime": "timestamp",
        "Name": "string",
        "OwnerId": "string",
        "ProfileId": "string",
        "ResourceId": "string",
        "Status": "CREATING|COMPLETE|DELETING|UPDATING|DELETED|FAILED",
        "StatusMessage": "string"
    }
}
```

---

### 7.6 `disassociate-profile`

Removes a Route 53 Profile association from a VPC.

**Synopsis:**
```bash
aws route53profiles disassociate-profile \
    --profile-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | The profile ID (max 64 chars) |
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |

**Output Schema:**
Same as `associate-profile` output.

---

### 7.7 `get-profile-association`

Gets details of a profile-VPC association.

**Synopsis:**
```bash
aws route53profiles get-profile-association \
    --profile-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |

**Output Schema:**
Same as `associate-profile` output.

---

### 7.8 `list-profile-associations`

Lists all profile-VPC associations. **Paginated.**

**Synopsis:**
```bash
aws route53profiles list-profile-associations \
    [--profile-id <value>] \
    [--resource-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | No | string | None | Filter by profile ID |
| `--resource-id` | No | string | None | Filter by VPC ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProfileAssociations": [{"...same as ProfileAssociation above..."}],
    "NextToken": "string"
}
```

---

### 7.9 `associate-resource-to-profile`

Associates a DNS resource (firewall rule group, private hosted zone, resolver rule) with a Route 53 Profile.

**Synopsis:**
```bash
aws route53profiles associate-resource-to-profile \
    --name <value> \
    --profile-id <value> \
    --resource-arn <value> \
    [--resource-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Association name (max 64 chars) |
| `--profile-id` | **Yes** | string | -- | The profile ID (max 64 chars) |
| `--resource-arn` | **Yes** | string | -- | ARN of the DNS resource (max 255 chars) |
| `--resource-properties` | No | string | None | Resource-specific properties (e.g., `{"priority": 102}` for firewall rule groups, priority range 100-9900) |

**Output Schema:**
```json
{
    "ProfileResourceAssociation": {
        "CreationTime": "timestamp",
        "Id": "string",
        "ModificationTime": "timestamp",
        "Name": "string",
        "OwnerId": "string",
        "ProfileId": "string",
        "ResourceArn": "string",
        "ResourceProperties": "string",
        "ResourceType": "string",
        "Status": "COMPLETE|DELETING|UPDATING|CREATING|DELETED|FAILED",
        "StatusMessage": "string"
    }
}
```

**Resource Types:** `FIREWALL_RULE_GROUP`, `PRIVATE_HOSTED_ZONE`, `RESOLVER_RULE`

---

### 7.10 `disassociate-resource-from-profile`

Removes a DNS resource association from a Route 53 Profile.

**Synopsis:**
```bash
aws route53profiles disassociate-resource-from-profile \
    --profile-id <value> \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | The profile ID (max 64 chars) |
| `--resource-arn` | **Yes** | string | -- | ARN of the DNS resource (max 255 chars) |

**Output Schema:**
Same as `associate-resource-to-profile` output.

---

### 7.11 `get-profile-resource-association`

Gets details of a resource-profile association.

**Synopsis:**
```bash
aws route53profiles get-profile-resource-association \
    --profile-resource-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-resource-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |

**Output Schema:**
Same as `associate-resource-to-profile` output.

---

### 7.12 `list-profile-resource-associations`

Lists all resource associations for a profile. **Paginated.**

**Synopsis:**
```bash
aws route53profiles list-profile-resource-associations \
    --profile-id <value> \
    [--resource-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | The profile ID (max 64 chars) |
| `--resource-type` | No | string | None | Filter by resource type |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProfileResourceAssociations": [{"...same as ProfileResourceAssociation above..."}],
    "NextToken": "string"
}
```

---

### 7.13 `update-profile-resource-association`

Updates a resource-profile association (name or resource properties).

**Synopsis:**
```bash
aws route53profiles update-profile-resource-association \
    --profile-resource-association-id <value> \
    [--name <value>] \
    [--resource-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-resource-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |
| `--name` | No | string | None | New association name (max 64 chars) |
| `--resource-properties` | No | string | None | New resource properties (e.g., `{"priority": 200}`) |

**Output Schema:**
Same as `associate-resource-to-profile` output.
