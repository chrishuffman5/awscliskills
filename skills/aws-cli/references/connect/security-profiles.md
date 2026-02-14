# Security Profiles

### 11.1 `create-security-profile`

Creates a security profile.

**Synopsis:**
```bash
aws connect create-security-profile \
    --security-profile-name <value> \
    --instance-id <value> \
    [--description <value>] \
    [--permissions <value>] \
    [--tags <value>] \
    [--allowed-access-control-tags <value>] \
    [--tag-restricted-resources <value>] \
    [--applications <value>] \
    [--hierarchy-restricted-resources <value>] \
    [--allowed-access-control-hierarchy-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name (1-127 chars) |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--description` | No | string | None | Description (max 250 chars) |
| `--permissions` | No | list | None | Permissions (max 500) |
| `--tags` | No | map | None | Tags (max 50) |
| `--allowed-access-control-tags` | No | map | None | ABAC tags (max 4) |
| `--tag-restricted-resources` | No | list | None | Resources with tag restrictions (max 10) |
| `--applications` | No | list | None | Third-party apps (max 10) |
| `--hierarchy-restricted-resources` | No | list | None | Hierarchy-restricted resources |
| `--allowed-access-control-hierarchy-group-id` | No | string | None | Hierarchy group for access |

**Output Schema:**
```json
{
    "SecurityProfileId": "string",
    "SecurityProfileArn": "string"
}
```

---

### 11.2 `describe-security-profile`

Describes a security profile.

**Synopsis:**
```bash
aws connect describe-security-profile \
    --security-profile-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-id` | **Yes** | string | -- | Security profile ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output Schema:**
```json
{
    "SecurityProfile": {
        "Id": "string",
        "OrganizationResourceId": "string",
        "Arn": "string",
        "SecurityProfileName": "string",
        "Description": "string",
        "Tags": { "key": "value" },
        "AllowedAccessControlTags": {},
        "TagRestrictedResources": [],
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string",
        "HierarchyRestrictedResources": [],
        "AllowedAccessControlHierarchyGroupId": "string"
    }
}
```

---

### 11.3 `list-security-profiles`

Lists security profiles. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-security-profiles \
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
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "SecurityProfileSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 11.4 `update-security-profile`

Updates a security profile.

**Synopsis:**
```bash
aws connect update-security-profile \
    --security-profile-id <value> \
    --instance-id <value> \
    [--description <value>] \
    [--permissions <value>] \
    [--allowed-access-control-tags <value>] \
    [--tag-restricted-resources <value>] \
    [--applications <value>] \
    [--hierarchy-restricted-resources <value>] \
    [--allowed-access-control-hierarchy-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-id` | **Yes** | string | -- | Security profile ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--description` | No | string | None | Updated description |
| `--permissions` | No | list | None | Updated permissions |
| `--allowed-access-control-tags` | No | map | None | Updated ABAC tags |
| `--tag-restricted-resources` | No | list | None | Updated restricted resources |
| `--applications` | No | list | None | Updated apps |
| `--hierarchy-restricted-resources` | No | list | None | Updated hierarchy resources |
| `--allowed-access-control-hierarchy-group-id` | No | string | None | Updated hierarchy group |

**Output:** None

---

### 11.5 `delete-security-profile`

Deletes a security profile.

**Synopsis:**
```bash
aws connect delete-security-profile \
    --instance-id <value> \
    --security-profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--security-profile-id` | **Yes** | string | -- | Security profile ID |

**Output:** None

---

### 11.6 `search-security-profiles`

Searches security profiles. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-security-profiles \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--search-criteria <value>] \
    [--search-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-criteria` | No | structure | None | Search criteria |
| `--search-filter` | No | structure | None | Tag filter |

**Output Schema:**
```json
{
    "SecurityProfiles": [ { "Id": "string", "OrganizationResourceId": "string", "Arn": "string", "SecurityProfileName": "string", "Description": "string", "Tags": {}, "AllowedAccessControlTags": {}, "TagRestrictedResources": [] } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```

---

### 11.7 `list-security-profile-permissions`

Lists permissions for a security profile. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-security-profile-permissions \
    --security-profile-id <value> \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-id` | **Yes** | string | -- | Security profile ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "Permissions": ["string"],
    "NextToken": "string",
    "LastModifiedTime": "timestamp",
    "LastModifiedRegion": "string"
}
```

---

### 11.8-11.12 Additional Security Profile Commands

`list-security-profile-applications`, `list-security-profile-flow-modules`, `list-security-keys`, `associate-security-key`, `disassociate-security-key`, `associate-security-profiles`, `disassociate-security-profiles`, `list-entity-security-profiles` follow the standard pattern with `--instance-id` and relevant security profile/key parameters.

**associate-security-key output:**
```json
{
    "AssociationId": "string"
}
```
