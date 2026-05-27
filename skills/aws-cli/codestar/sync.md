# Sync

### 4.1 `create-sync-configuration`

Creates a sync configuration linking a repository to a resource (e.g., CloudFormation stack).

**Synopsis:**
```bash
aws codestar-connections create-sync-configuration \
    --branch <value> \
    --config-file <value> \
    --repository-link-id <value> \
    --resource-name <value> \
    --role-arn <value> \
    --sync-type <value> \
    [--publish-deployment-status <value>] \
    [--trigger-resource-update-on <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--branch` | **Yes** | string | -- | Branch name to sync from |
| `--config-file` | **Yes** | string | -- | Path to the configuration file in the repository |
| `--repository-link-id` | **Yes** | string | -- | ID of the repository link |
| `--resource-name` | **Yes** | string | -- | Name of the resource to sync to |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for the sync operation |
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |
| `--publish-deployment-status` | No | string | None | Whether to publish deployment status: `ENABLED`, `DISABLED` |
| `--trigger-resource-update-on` | No | string | None | When to trigger updates: `ANY_CHANGE`, `FILE_CHANGE` |

**Output Schema:**
```json
{
    "SyncConfiguration": {
        "Branch": "string",
        "ConfigFile": "string",
        "OwnerId": "string",
        "ProviderType": "Bitbucket|GitHub|GitHubEnterpriseServer|GitLab|GitLabSelfManaged",
        "RepositoryLinkId": "string",
        "RepositoryName": "string",
        "ResourceName": "string",
        "RoleArn": "string",
        "SyncType": "CFN_STACK_SYNC",
        "PublishDeploymentStatus": "ENABLED|DISABLED",
        "TriggerResourceUpdateOn": "ANY_CHANGE|FILE_CHANGE"
    }
}
```

---

### 4.2 `delete-sync-configuration`

Deletes a sync configuration.

**Synopsis:**
```bash
aws codestar-connections delete-sync-configuration \
    --sync-type <value> \
    --resource-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |
| `--resource-name` | **Yes** | string | -- | Name of the resource |

**Output Schema:**
```json
{}
```

---

### 4.3 `get-sync-configuration`

Returns details of a sync configuration.

**Synopsis:**
```bash
aws codestar-connections get-sync-configuration \
    --sync-type <value> \
    --resource-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |
| `--resource-name` | **Yes** | string | -- | Name of the resource |

**Output Schema:**
```json
{
    "SyncConfiguration": {
        "Branch": "string",
        "ConfigFile": "string",
        "OwnerId": "string",
        "ProviderType": "string",
        "RepositoryLinkId": "string",
        "RepositoryName": "string",
        "ResourceName": "string",
        "RoleArn": "string",
        "SyncType": "CFN_STACK_SYNC",
        "PublishDeploymentStatus": "ENABLED|DISABLED",
        "TriggerResourceUpdateOn": "ANY_CHANGE|FILE_CHANGE"
    }
}
```

---

### 4.4 `list-sync-configurations`

Lists sync configurations for a repository link. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-connections list-sync-configurations \
    --repository-link-id <value> \
    --sync-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-link-id` | **Yes** | string | -- | ID of the repository link |
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SyncConfigurations": [
        {
            "Branch": "string",
            "ConfigFile": "string",
            "OwnerId": "string",
            "ProviderType": "string",
            "RepositoryLinkId": "string",
            "RepositoryName": "string",
            "ResourceName": "string",
            "RoleArn": "string",
            "SyncType": "CFN_STACK_SYNC",
            "PublishDeploymentStatus": "string",
            "TriggerResourceUpdateOn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-sync-configuration`

Updates a sync configuration.

**Synopsis:**
```bash
aws codestar-connections update-sync-configuration \
    --resource-name <value> \
    --sync-type <value> \
    [--branch <value>] \
    [--config-file <value>] \
    [--repository-link-id <value>] \
    [--role-arn <value>] \
    [--publish-deployment-status <value>] \
    [--trigger-resource-update-on <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |
| `--branch` | No | string | None | Updated branch name |
| `--config-file` | No | string | None | Updated config file path |
| `--repository-link-id` | No | string | None | Updated repository link ID |
| `--role-arn` | No | string | None | Updated IAM role ARN |
| `--publish-deployment-status` | No | string | None | `ENABLED` or `DISABLED` |
| `--trigger-resource-update-on` | No | string | None | `ANY_CHANGE` or `FILE_CHANGE` |

**Output Schema:**
```json
{
    "SyncConfiguration": {
        "Branch": "string",
        "ConfigFile": "string",
        "OwnerId": "string",
        "ProviderType": "string",
        "RepositoryLinkId": "string",
        "RepositoryName": "string",
        "ResourceName": "string",
        "RoleArn": "string",
        "SyncType": "CFN_STACK_SYNC",
        "PublishDeploymentStatus": "string",
        "TriggerResourceUpdateOn": "string"
    }
}
```

---

### 4.6 `get-resource-sync-status`

Returns the sync status of a resource.

**Synopsis:**
```bash
aws codestar-connections get-resource-sync-status \
    --resource-name <value> \
    --sync-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |

**Output Schema:**
```json
{
    "DesiredState": {
        "Branch": "string",
        "Directory": "string",
        "OwnerId": "string",
        "RepositoryName": "string",
        "ProviderType": "string",
        "Sha": "string"
    },
    "LatestSuccessfulSync": {
        "Events": [
            {
                "Event": "string",
                "ExternalId": "string",
                "Time": "timestamp",
                "Type": "string"
            }
        ],
        "InitialRevision": {
            "Branch": "string",
            "Directory": "string",
            "OwnerId": "string",
            "RepositoryName": "string",
            "ProviderType": "string",
            "Sha": "string"
        },
        "StartedAt": "timestamp",
        "Status": "FAILED|INITIATED|IN_PROGRESS|SUCCEEDED|QUEUED",
        "TargetRevision": {
            "Branch": "string",
            "Directory": "string",
            "OwnerId": "string",
            "RepositoryName": "string",
            "ProviderType": "string",
            "Sha": "string"
        },
        "Target": "string"
    },
    "LatestSync": {
        "Events": [],
        "InitialRevision": {},
        "StartedAt": "timestamp",
        "Status": "string",
        "TargetRevision": {},
        "Target": "string"
    }
}
```

---

### 4.7 `get-sync-blocker-summary`

Returns a summary of sync blockers for a resource and sync type.

**Synopsis:**
```bash
aws codestar-connections get-sync-blocker-summary \
    --sync-type <value> \
    --resource-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |
| `--resource-name` | **Yes** | string | -- | Name of the resource |

**Output Schema:**
```json
{
    "SyncBlockerSummary": {
        "ResourceName": "string",
        "ParentResourceName": "string",
        "LatestBlockers": [
            {
                "Id": "string",
                "Type": "AUTOMATED",
                "Status": "ACTIVE|RESOLVED",
                "CreatedReason": "string",
                "CreatedAt": "timestamp",
                "Contexts": [
                    {
                        "Key": "string",
                        "Value": "string"
                    }
                ],
                "ResolvedReason": "string",
                "ResolvedAt": "timestamp"
            }
        ]
    }
}
```

---

### 4.8 `update-sync-blocker`

Updates or resolves a sync blocker.

**Synopsis:**
```bash
aws codestar-connections update-sync-blocker \
    --id <value> \
    --sync-type <value> \
    --resource-name <value> \
    --resolved-reason <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the sync blocker |
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--resolved-reason` | **Yes** | string | -- | Reason for resolving the blocker |

**Output Schema:**
```json
{
    "ResourceName": "string",
    "ParentResourceName": "string",
    "SyncBlocker": {
        "Id": "string",
        "Type": "AUTOMATED",
        "Status": "ACTIVE|RESOLVED",
        "CreatedReason": "string",
        "CreatedAt": "timestamp",
        "Contexts": [],
        "ResolvedReason": "string",
        "ResolvedAt": "timestamp"
    }
}
```
