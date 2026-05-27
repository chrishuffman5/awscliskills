# Connections

### 1.1 `create-connection`

Creates a connection to a third-party code repository provider (GitHub, Bitbucket, GitLab). After creation, the connection is in `PENDING` status and must be completed via the AWS console.

**Synopsis:**
```bash
aws codestar-connections create-connection \
    --provider-type <value> \
    --connection-name <value> \
    [--tags <value>] \
    [--host-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider-type` | **Yes** | string | -- | Provider type: `Bitbucket`, `GitHub`, `GitHubEnterpriseServer`, `GitLab`, `GitLabSelfManaged` |
| `--connection-name` | **Yes** | string | -- | Name of the connection |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--host-arn` | No | string | None | ARN of the host for enterprise/self-managed providers |

**Output Schema:**
```json
{
    "ConnectionArn": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 1.2 `delete-connection`

Deletes a connection. The associated provider-specific authorization is also deleted.

**Synopsis:**
```bash
aws codestar-connections delete-connection \
    --connection-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-arn` | **Yes** | string | -- | ARN of the connection to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `get-connection`

Returns the details of a connection.

**Synopsis:**
```bash
aws codestar-connections get-connection \
    --connection-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-arn` | **Yes** | string | -- | ARN of the connection |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionName": "string",
        "ConnectionArn": "string",
        "ProviderType": "Bitbucket|GitHub|GitHubEnterpriseServer|GitLab|GitLabSelfManaged",
        "OwnerAccountId": "string",
        "ConnectionStatus": "PENDING|AVAILABLE|ERROR",
        "HostArn": "string"
    }
}
```

---

### 1.4 `list-connections`

Lists connections in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-connections list-connections \
    [--provider-type-filter <value>] \
    [--host-arn-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider-type-filter` | No | string | None | Filter by provider type |
| `--host-arn-filter` | No | string | None | Filter by host ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Connections": [
        {
            "ConnectionName": "string",
            "ConnectionArn": "string",
            "ProviderType": "Bitbucket|GitHub|GitHubEnterpriseServer|GitLab|GitLabSelfManaged",
            "OwnerAccountId": "string",
            "ConnectionStatus": "PENDING|AVAILABLE|ERROR",
            "HostArn": "string"
        }
    ],
    "NextToken": "string"
}
```
