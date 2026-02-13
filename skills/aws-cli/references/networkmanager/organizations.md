# Organizations

### 12.1 `list-organization-service-access-status`

Gets the status of the Service Linked Role (SLR) for the caller's organization.

**Synopsis:**
```bash
aws networkmanager list-organization-service-access-status \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationStatus": {
        "OrganizationId": "string",
        "OrganizationAwsServiceAccessStatus": "string",
        "SLRDeploymentStatus": "string",
        "AccountStatusList": [
            {
                "AccountId": "string",
                "SLRDeploymentStatus": "string"
            }
        ]
    },
    "NextToken": "string"
}
```

---

### 12.2 `start-organization-service-access-update`

Enables or disables Network Manager for the caller's organization. This creates the required service-linked roles.

**Synopsis:**
```bash
aws networkmanager start-organization-service-access-update \
    --action <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action` | **Yes** | string | -- | Action: `ENABLE` or `DISABLE` |

**Output Schema:**
```json
{
    "OrganizationStatus": {
        "OrganizationId": "string",
        "OrganizationAwsServiceAccessStatus": "string",
        "SLRDeploymentStatus": "string",
        "AccountStatusList": [
            {
                "AccountId": "string",
                "SLRDeploymentStatus": "string"
            }
        ]
    }
}
```
