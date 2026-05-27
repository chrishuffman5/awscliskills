# Settings

### 10.1 `get-global-settings`

Retrieves global settings for the account.

**Synopsis:**
```bash
aws wellarchitected get-global-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| (none) | -- | -- | -- | No parameters required |

**Output Schema:**
```json
{
    "OrganizationSharingStatus": "ENABLED|DISABLED",
    "DiscoveryIntegrationStatus": "ENABLED|DISABLED",
    "JiraConfiguration": {
        "IntegrationStatus": "CONFIGURED|NOT_CONFIGURED",
        "IssueManagementStatus": "ENABLED|DISABLED",
        "IssueManagementType": "AUTO|MANUAL",
        "Subdomain": "string",
        "JiraProjectKey": "string",
        "StatusMessage": "string"
    }
}
```

---

### 10.2 `update-global-settings`

Updates global settings for the account.

**Synopsis:**
```bash
aws wellarchitected update-global-settings \
    [--organization-sharing-status <value>] \
    [--discovery-integration-status <value>] \
    [--jira-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-sharing-status` | No | string | None | `ENABLED` or `DISABLED` |
| `--discovery-integration-status` | No | string | None | `ENABLED` or `DISABLED` |
| `--jira-configuration` | No | structure | None | Jira settings. Shorthand: `IntegrationStatus=CONFIGURED\|NOT_CONFIGURED,IssueManagementStatus=ENABLED\|DISABLED,IssueManagementType=AUTO\|MANUAL,Subdomain=string,JiraProjectKey=string` |

**Output Schema:**
```json
None
```

---

### 10.3 `update-integration`

Updates integration settings (Jira) for a workload.

**Synopsis:**
```bash
aws wellarchitected update-integration \
    --workload-id <value> \
    --client-request-token <value> \
    --integrating-service <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |
| `--integrating-service` | **Yes** | string | -- | `JIRA` |

**Output Schema:**
```json
None
```
