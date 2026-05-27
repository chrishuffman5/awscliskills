# Account Settings

### 8.1 `register-account`

Registers the calling account with AWS Audit Manager.

**Synopsis:**
```bash
aws auditmanager register-account \
    [--kms-key <value>] \
    [--delegated-admin-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--kms-key` | No | string | None | KMS key ARN or alias for encryption |
| `--delegated-admin-account` | No | string | None | Delegated admin account ID (12 digits) |

**Output Schema:**
```json
{
    "status": "ACTIVE|INACTIVE|PENDING_ACTIVATION"
}
```

---

### 8.2 `deregister-account`

Deregisters the calling account from Audit Manager.

**Synopsis:**
```bash
aws auditmanager deregister-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "status": "ACTIVE|INACTIVE|PENDING_ACTIVATION"
}
```

---

### 8.3 `get-account-status`

Returns the registration status of the calling account.

**Synopsis:**
```bash
aws auditmanager get-account-status \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "status": "ACTIVE|INACTIVE|PENDING_ACTIVATION"
}
```

---

### 8.4 `get-settings`

Returns the Audit Manager settings for the account.

**Synopsis:**
```bash
aws auditmanager get-settings \
    --attribute <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attribute` | **Yes** | string | -- | Setting attribute: `ALL`, `IS_AWS_ORG_ENABLED`, `SNS_TOPIC`, `DEFAULT_ASSESSMENT_REPORTS_DESTINATION`, `DEFAULT_PROCESS_OWNERS`, `EVIDENCE_FINDER_ENABLEMENT`, `DEREGISTRATION_POLICY`, `DEFAULT_EXPORT_DESTINATION` |

**Output Schema:**
```json
{
    "settings": {
        "isAwsOrgEnabled": true|false,
        "snsTopic": "string",
        "defaultAssessmentReportsDestination": {
            "destinationType": "S3",
            "destination": "string"
        },
        "defaultProcessOwners": [
            {
                "roleType": "PROCESS_OWNER|RESOURCE_OWNER",
                "roleArn": "string"
            }
        ],
        "kmsKey": "string",
        "evidenceFinderEnablement": {
            "eventDataStoreArn": "string",
            "enablementStatus": "ENABLED|DISABLED|ENABLE_IN_PROGRESS|DISABLE_IN_PROGRESS",
            "backfillStatus": "NOT_STARTED|IN_PROGRESS|COMPLETED",
            "error": "string"
        },
        "deregistrationPolicy": {
            "deleteResources": "ALL|DEFAULT"
        },
        "defaultExportDestination": {
            "destinationType": "S3",
            "destination": "string"
        }
    }
}
```

---

### 8.5 `update-settings`

Updates Audit Manager settings for the account.

**Synopsis:**
```bash
aws auditmanager update-settings \
    [--sns-topic <value>] \
    [--default-assessment-reports-destination <value>] \
    [--default-process-owners <value>] \
    [--kms-key <value>] \
    [--evidence-finder-enabled | --no-evidence-finder-enabled] \
    [--deregistration-policy <value>] \
    [--default-export-destination <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sns-topic` | No | string | None | SNS topic ARN for notifications |
| `--default-assessment-reports-destination` | No | structure | None | Default S3 destination for reports |
| `--default-process-owners` | No | list | None | Default process owner roles |
| `--kms-key` | No | string | None | KMS key ARN or alias |
| `--evidence-finder-enabled` | No | boolean | None | Enable/disable evidence finder |
| `--deregistration-policy` | No | structure | None | Deregistration policy: `deleteResources=ALL\|DEFAULT` |
| `--default-export-destination` | No | structure | None | Default export destination |

**Output Schema:** Same as `get-settings`.

---

### 8.6 `register-organization-admin-account`

Registers a delegated administrator for Audit Manager in AWS Organizations.

**Synopsis:**
```bash
aws auditmanager register-organization-admin-account \
    --admin-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account-id` | **Yes** | string | -- | Account ID to register as admin (12 digits) |

**Output Schema:**
```json
{
    "adminAccountId": "string",
    "organizationId": "string"
}
```

---

### 8.7 `deregister-organization-admin-account`

Deregisters the delegated administrator from Audit Manager.

**Synopsis:**
```bash
aws auditmanager deregister-organization-admin-account \
    [--admin-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account-id` | No | string | None | Admin account ID to deregister |

**Output Schema:** Empty on success.

---

### 8.8 `get-organization-admin-account`

Returns the delegated administrator account for Audit Manager.

**Synopsis:**
```bash
aws auditmanager get-organization-admin-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "adminAccountId": "string",
    "organizationId": "string"
}
```

---

### 8.9 `list-notifications`

Returns a list of Audit Manager notifications. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-notifications \
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
    "notifications": [
        {
            "id": "string",
            "assessmentId": "string",
            "assessmentName": "string",
            "controlSetId": "string",
            "controlSetName": "string",
            "description": "string",
            "eventTime": "timestamp",
            "source": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.10 `tag-resource`

Adds tags to an Audit Manager resource.

**Synopsis:**
```bash
aws auditmanager tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags. Shorthand: `KeyName1=string,KeyName2=string` (max 50, keys 1-128 chars, values 0-256 chars) |

**Output Schema:** Empty on success.

---

### 8.11 `untag-resource`

Removes tags from an Audit Manager resource.

**Synopsis:**
```bash
aws auditmanager untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:** Empty on success.

---

### 8.12 `list-tags-for-resource`

Lists the tags on an Audit Manager resource.

**Synopsis:**
```bash
aws auditmanager list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": {
        "key": "value"
    }
}
```
