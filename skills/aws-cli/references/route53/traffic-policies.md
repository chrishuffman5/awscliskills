# Traffic Policies

### 4.1 `create-traffic-policy`

Creates a traffic policy, which defines how Route 53 responds to DNS queries using routing rules.

**Synopsis:**
```bash
aws route53 create-traffic-policy \
    --name <value> \
    --document <value> \
    [--comment <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Traffic policy name (max 512 chars) |
| `--document` | **Yes** | string | -- | Traffic policy JSON definition (max 102400 chars). Supports `file://` syntax |
| `--comment` | No | string | None | Comment (max 1024 chars) |

**Output Schema:**
```json
{
    "TrafficPolicy": {
        "Id": "string",
        "Version": "integer",
        "Name": "string",
        "Type": "A|AAAA|CNAME|MX|TXT|NS|SOA|SRV|CAA|DS|NAPTR|PTR|SPF|TLSA|SSHFP|SVCB|HTTPS",
        "Document": "string",
        "Comment": "string"
    },
    "Location": "string"
}
```

---

### 4.2 `create-traffic-policy-version`

Creates a new version of an existing traffic policy.

**Synopsis:**
```bash
aws route53 create-traffic-policy-version \
    --id <value> \
    --document <value> \
    [--comment <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--document` | **Yes** | string | -- | Traffic policy JSON definition (max 102400 chars) |
| `--comment` | No | string | None | Comment (max 1024 chars) |

**Output Schema:**
```json
{
    "TrafficPolicy": {
        "Id": "string",
        "Version": "integer",
        "Name": "string",
        "Type": "string",
        "Document": "string",
        "Comment": "string"
    },
    "Location": "string"
}
```

---

### 4.3 `get-traffic-policy`

Gets information about a specific traffic policy version.

**Synopsis:**
```bash
aws route53 get-traffic-policy \
    --id <value> \
    --version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--version` | **Yes** | integer | -- | Version number (1-1000) |

**Output Schema:**
```json
{
    "TrafficPolicy": {
        "Id": "string",
        "Version": "integer",
        "Name": "string",
        "Type": "string",
        "Document": "string",
        "Comment": "string"
    }
}
```

---

### 4.4 `delete-traffic-policy`

Deletes a specific version of a traffic policy. All instances must be deleted first.

**Synopsis:**
```bash
aws route53 delete-traffic-policy \
    --id <value> \
    --version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--version` | **Yes** | integer | -- | Version number (1-1000) |

**Output:** None on success.

---

### 4.5 `list-traffic-policies`

Lists all traffic policies in the account.

**Synopsis:**
```bash
aws route53 list-traffic-policies \
    [--traffic-policy-id-marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--traffic-policy-id-marker` | No | string | None | Start listing from this policy ID (1-36 chars) |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "TrafficPolicySummaries": [
        {
            "Id": "string",
            "Name": "string",
            "Type": "string",
            "LatestVersion": "integer",
            "TrafficPolicyCount": "integer"
        }
    ],
    "IsTruncated": true|false,
    "TrafficPolicyIdMarker": "string",
    "MaxItems": "string"
}
```

---

### 4.6 `list-traffic-policy-versions`

Lists all versions of a specific traffic policy.

**Synopsis:**
```bash
aws route53 list-traffic-policy-versions \
    --id <value> \
    [--traffic-policy-version-marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--traffic-policy-version-marker` | No | string | None | Start listing from this version |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "TrafficPolicies": [
        {
            "Id": "string",
            "Version": "integer",
            "Name": "string",
            "Type": "string",
            "Document": "string",
            "Comment": "string"
        }
    ],
    "IsTruncated": true|false,
    "TrafficPolicyVersionMarker": "string",
    "MaxItems": "string"
}
```

---

### 4.7 `update-traffic-policy-comment`

Updates the comment for a specified traffic policy version.

**Synopsis:**
```bash
aws route53 update-traffic-policy-comment \
    --id <value> \
    --version <value> \
    --comment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--version` | **Yes** | integer | -- | Version number (1-1000) |
| `--comment` | **Yes** | string | -- | New comment (max 1024 chars) |

**Output Schema:**
```json
{
    "TrafficPolicy": {
        "Id": "string",
        "Version": "integer",
        "Name": "string",
        "Type": "string",
        "Document": "string",
        "Comment": "string"
    }
}
```

---

### 4.8 `create-traffic-policy-instance`

Creates DNS records in a hosted zone based on a traffic policy.

**Synopsis:**
```bash
aws route53 create-traffic-policy-instance \
    --hosted-zone-id <value> \
    --name <value> \
    --ttl <value> \
    --traffic-policy-id <value> \
    --traffic-policy-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--name` | **Yes** | string | -- | Domain name for the records (max 1024 chars) |
| `--ttl` | **Yes** | long | -- | TTL for created records (0-2147483647) |
| `--traffic-policy-id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--traffic-policy-version` | **Yes** | integer | -- | Policy version (1-1000) |

**Output Schema:**
```json
{
    "TrafficPolicyInstance": {
        "Id": "string",
        "HostedZoneId": "string",
        "Name": "string",
        "TTL": "long",
        "State": "Applied|Creating|Failed",
        "Message": "string",
        "TrafficPolicyId": "string",
        "TrafficPolicyVersion": "integer",
        "TrafficPolicyType": "string"
    },
    "Location": "string"
}
```

---

### 4.9 `get-traffic-policy-instance`

Gets information about a specified traffic policy instance.

**Synopsis:**
```bash
aws route53 get-traffic-policy-instance \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy instance ID (1-36 chars) |

**Output Schema:**
```json
{
    "TrafficPolicyInstance": {
        "Id": "string",
        "HostedZoneId": "string",
        "Name": "string",
        "TTL": "long",
        "State": "Applied|Creating|Failed",
        "Message": "string",
        "TrafficPolicyId": "string",
        "TrafficPolicyVersion": "integer",
        "TrafficPolicyType": "string"
    }
}
```

---

### 4.10 `delete-traffic-policy-instance`

Deletes a traffic policy instance and all associated DNS records.

**Synopsis:**
```bash
aws route53 delete-traffic-policy-instance \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy instance ID (1-36 chars) |

**Output:** None on success.

---

### 4.11 `list-traffic-policy-instances`

Lists all traffic policy instances in the account.

**Synopsis:**
```bash
aws route53 list-traffic-policy-instances \
    [--hosted-zone-id-marker <value>] \
    [--traffic-policy-instance-name-marker <value>] \
    [--traffic-policy-instance-type-marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id-marker` | No | string | None | Start from this hosted zone (max 32 chars) |
| `--traffic-policy-instance-name-marker` | No | string | None | Start from this instance name (max 1024 chars) |
| `--traffic-policy-instance-type-marker` | No | string | None | Start from this record type |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "TrafficPolicyInstances": [
        {
            "Id": "string",
            "HostedZoneId": "string",
            "Name": "string",
            "TTL": "long",
            "State": "Applied|Creating|Failed",
            "Message": "string",
            "TrafficPolicyId": "string",
            "TrafficPolicyVersion": "integer",
            "TrafficPolicyType": "string"
        }
    ],
    "HostedZoneIdMarker": "string",
    "TrafficPolicyInstanceNameMarker": "string",
    "TrafficPolicyInstanceTypeMarker": "string",
    "IsTruncated": true|false,
    "MaxItems": "string"
}
```

---

### 4.12 `list-traffic-policy-instances-by-hosted-zone`

Lists traffic policy instances for a specific hosted zone.

**Synopsis:**
```bash
aws route53 list-traffic-policy-instances-by-hosted-zone \
    --hosted-zone-id <value> \
    [--traffic-policy-instance-name-marker <value>] \
    [--traffic-policy-instance-type-marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--traffic-policy-instance-name-marker` | No | string | None | Start from this instance name |
| `--traffic-policy-instance-type-marker` | No | string | None | Start from this record type |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "TrafficPolicyInstances": [
        {
            "Id": "string",
            "HostedZoneId": "string",
            "Name": "string",
            "TTL": "long",
            "State": "Applied|Creating|Failed",
            "Message": "string",
            "TrafficPolicyId": "string",
            "TrafficPolicyVersion": "integer",
            "TrafficPolicyType": "string"
        }
    ],
    "TrafficPolicyInstanceNameMarker": "string",
    "TrafficPolicyInstanceTypeMarker": "string",
    "IsTruncated": true|false,
    "MaxItems": "string"
}
```

---

### 4.13 `list-traffic-policy-instances-by-policy`

Lists traffic policy instances for a specific traffic policy and version.

**Synopsis:**
```bash
aws route53 list-traffic-policy-instances-by-policy \
    --traffic-policy-id <value> \
    --traffic-policy-version <value> \
    [--hosted-zone-id-marker <value>] \
    [--traffic-policy-instance-name-marker <value>] \
    [--traffic-policy-instance-type-marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--traffic-policy-id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--traffic-policy-version` | **Yes** | integer | -- | Policy version (1-1000) |
| `--hosted-zone-id-marker` | No | string | None | Start from this hosted zone |
| `--traffic-policy-instance-name-marker` | No | string | None | Start from this instance name |
| `--traffic-policy-instance-type-marker` | No | string | None | Start from this record type |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "TrafficPolicyInstances": [
        {
            "Id": "string",
            "HostedZoneId": "string",
            "Name": "string",
            "TTL": "long",
            "State": "Applied|Creating|Failed",
            "Message": "string",
            "TrafficPolicyId": "string",
            "TrafficPolicyVersion": "integer",
            "TrafficPolicyType": "string"
        }
    ],
    "HostedZoneIdMarker": "string",
    "TrafficPolicyInstanceNameMarker": "string",
    "TrafficPolicyInstanceTypeMarker": "string",
    "IsTruncated": true|false,
    "MaxItems": "string"
}
```

---

### 4.14 `update-traffic-policy-instance`

Updates the traffic policy version and TTL for an existing traffic policy instance. Route 53 creates new records based on the updated policy.

**Synopsis:**
```bash
aws route53 update-traffic-policy-instance \
    --id <value> \
    --ttl <value> \
    --traffic-policy-id <value> \
    --traffic-policy-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Traffic policy instance ID (1-36 chars) |
| `--ttl` | **Yes** | long | -- | TTL for records (0-2147483647) |
| `--traffic-policy-id` | **Yes** | string | -- | Traffic policy ID (1-36 chars) |
| `--traffic-policy-version` | **Yes** | integer | -- | Policy version (1-1000) |

**Output Schema:**
```json
{
    "TrafficPolicyInstance": {
        "Id": "string",
        "HostedZoneId": "string",
        "Name": "string",
        "TTL": "long",
        "State": "Applied|Creating|Failed",
        "Message": "string",
        "TrafficPolicyId": "string",
        "TrafficPolicyVersion": "integer",
        "TrafficPolicyType": "string"
    }
}
```

---

### 4.15 `get-traffic-policy-instance-count`

Returns the total number of traffic policy instances in the account.

**Synopsis:**
```bash
aws route53 get-traffic-policy-instance-count \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options).

**Output Schema:**
```json
{
    "TrafficPolicyInstanceCount": "integer"
}
```

---
