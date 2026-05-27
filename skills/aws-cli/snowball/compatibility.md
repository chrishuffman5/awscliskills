# Compatibility

### 5.1 `get-snowball-usage`

Returns the account's Snow device usage limits and current usage count. No parameters required.

**Synopsis:**
```bash
aws snowball get-snowball-usage \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "SnowballLimit": "integer",
    "SnowballsInUse": "integer"
}
```

| Field | Description |
|-------|-------------|
| `SnowballLimit` | Service limit for number of Snow devices this account can have at once (default: 1) |
| `SnowballsInUse` | Number of Snow devices currently in use |

---

### 5.2 `list-compatible-images`

Returns a list of AMIs compatible with Snow Family devices. Supported images include Amazon Linux 2, Ubuntu 20.04 LTS, and Ubuntu 22.04 LTS. **Paginated operation.**

**Synopsis:**
```bash
aws snowball list-compatible-images \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CompatibleImages": [
        {
            "AmiId": "string",
            "Name": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.3 `list-service-versions`

Returns the supported versions of a service available on Snow Family devices (e.g., Kubernetes or EKS Anywhere versions).

**Synopsis:**
```bash
aws snowball list-service-versions \
    --service-name <value> \
    [--dependent-services <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Service name: `KUBERNETES`, `EKS_ANYWHERE` |
| `--dependent-services` | No | list | None | List of dependent services with their versions |
| `--max-results` | No | integer | None | Maximum results per page (0-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Dependent Services Shorthand:**
```bash
ServiceName=KUBERNETES,ServiceVersion={Version=1.24}
```

**Output Schema:**
```json
{
    "ServiceVersions": [
        {
            "Version": "string"
        }
    ],
    "ServiceName": "KUBERNETES|EKS_ANYWHERE",
    "DependentServices": [
        {
            "ServiceName": "KUBERNETES|EKS_ANYWHERE",
            "ServiceVersion": {
                "Version": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
