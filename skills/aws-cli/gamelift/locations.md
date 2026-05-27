# Locations

### 9.1 `create-location`

Creates a custom location for use with Anywhere fleets.

**Synopsis:**
```bash
aws gamelift create-location \
    --location-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-name` | **Yes** | string | -- | Custom location name (8-64 chars, must start with `custom-`) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Location": {
        "LocationName": "string",
        "LocationArn": "string"
    }
}
```

---

### 9.2 `delete-location`

Deletes a custom location.

**Synopsis:**
```bash
aws gamelift delete-location \
    --location-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-name` | **Yes** | string | -- | Custom location name or ARN |

**Output Schema:**
```json
None
```

---

### 9.3 `list-locations`

Lists all custom locations in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-locations \
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
| `--filters` | No | list(string) | None | Filter by type: `AWS` or `CUSTOM` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Locations": [
        {
            "LocationName": "string",
            "LocationArn": "string"
        }
    ],
    "NextToken": "string"
}
```
