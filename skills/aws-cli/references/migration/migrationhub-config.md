# Migration Hub Config

These commands use the `migrationhub-config` service namespace. They manage the Migration Hub home region, which must be set before using Migration Hub or Application Discovery Service.

> **Note:** Write actions (create, delete) must be executed in your home region. Read actions (describe, get) are permitted from any region.

### 10.1 `create-home-region-control`

Creates a home region control for your account.

**Synopsis:**
```bash
aws migrationhub-config create-home-region-control \
    --home-region <value> \
    --target <value> \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--home-region` | **Yes** | string | -- | AWS region name (e.g., `us-west-2`) |
| `--target` | **Yes** | structure | -- | Target account (see below) |
| `--dry-run` | No | boolean | None | Test permissions without making changes |

**Target Structure:**
```json
{
    "Type": "ACCOUNT",
    "Id": "123456789012"
}
```

Shorthand: `Type=ACCOUNT,Id=string`

**Output Schema:**
```json
{
    "HomeRegionControl": {
        "ControlId": "string",
        "HomeRegion": "string",
        "Target": {
            "Type": "ACCOUNT",
            "Id": "string"
        },
        "RequestedTime": "timestamp"
    }
}
```

---

### 10.2 `delete-home-region-control`

Deletes a home region control. Does not delete discovery or migration tracking data.

**Synopsis:**
```bash
aws migrationhub-config delete-home-region-control \
    --control-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-id` | **Yes** | string | -- | Control ID (pattern: `hrc-[a-z0-9]{12}`) |

**Output:** None

---

### 10.3 `describe-home-region-controls`

Describes home region controls. Returns details for all controls or filtered results.

**Synopsis:**
```bash
aws migrationhub-config describe-home-region-controls \
    [--control-id <value>] \
    [--home-region <value>] \
    [--target <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-id` | No | string | None | Filter by control ID |
| `--home-region` | No | string | None | Filter by home region |
| `--target` | No | structure | None | Filter by target account |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "HomeRegionControls": [
        {
            "ControlId": "string",
            "HomeRegion": "string",
            "Target": {
                "Type": "ACCOUNT",
                "Id": "string"
            },
            "RequestedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.4 `get-home-region`

Returns the calling account's configured home region.

**Synopsis:**
```bash
aws migrationhub-config get-home-region \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "HomeRegion": "string"
}
```
