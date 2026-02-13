# Hybrid AD

### 2.1 `connect-directory`

Creates an AD Connector to connect to a self-managed directory.

**Synopsis:**
```bash
aws ds connect-directory \
    --name <value> \
    --password <value> \
    --size <value> \
    --connect-settings <value> \
    [--short-name <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Fully qualified name of the self-managed directory |
| `--password` | **Yes** | string | -- | Password for the service account (1-128 chars) |
| `--size` | **Yes** | string | -- | `Small` or `Large` |
| `--connect-settings` | **Yes** | structure | -- | Connection settings |
| `--short-name` | No | string | None | NetBIOS name |
| `--description` | No | string | None | Description (max 128 chars) |
| `--tags` | No | list(structure) | None | Tags |
| `--network-type` | No | string | None | `Dual-stack`, `IPv4`, or `IPv6` |

**Connect Settings Structure:**
```json
{
    "VpcId": "string",
    "SubnetIds": ["string", "string"],
    "CustomerDnsIps": ["string"],
    "CustomerDnsIpsV6": ["string"],
    "CustomerUserName": "string"
}
```

**Output Schema:**
```json
{
    "DirectoryId": "string"
}
```

---

### 2.2 `create-hybrid-ad`

Creates a Hybrid AD setup. This allows you to extend an existing on-premises AD to AWS.

**Synopsis:**
```bash
aws ds create-hybrid-ad \
    --directory-id <value> \
    --dns-ip-addrs <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID of Managed Microsoft AD |
| `--dns-ip-addrs` | **Yes** | list(string) | -- | DNS IP addresses of the self-managed AD |
| `--tags` | No | list(structure) | None | Tags |

**Output Schema:**

No output on success (HTTP 200).

---

### 2.3 `describe-hybrid-ad-update`

Describes the status of hybrid AD updates. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-hybrid-ad-update \
    --directory-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "HybridAdUpdateActivities": [
        {
            "DirectoryId": "string",
            "Status": "string",
            "StatusReason": "string",
            "StartTime": "timestamp",
            "LastUpdatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-hybrid-ad`

Updates the hybrid AD configuration for a directory.

**Synopsis:**
```bash
aws ds update-hybrid-ad \
    --directory-id <value> \
    [--dns-ip-addrs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--dns-ip-addrs` | No | list(string) | None | Updated DNS IP addresses |

**Output Schema:**

No output on success (HTTP 200).
