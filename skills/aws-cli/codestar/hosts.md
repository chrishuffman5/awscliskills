# Hosts

### 2.1 `create-host`

Creates a host resource for connections to an installed provider (GitHub Enterprise Server, GitLab Self-Managed).

**Synopsis:**
```bash
aws codestar-connections create-host \
    --name <value> \
    --provider-type <value> \
    --provider-endpoint <value> \
    [--vpc-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the host (1-64 chars) |
| `--provider-type` | **Yes** | string | -- | Provider type: `GitHubEnterpriseServer`, `GitLabSelfManaged` |
| `--provider-endpoint` | **Yes** | string | -- | URL endpoint of the installed provider (e.g., `https://github.example.com`) |
| `--vpc-configuration` | No | structure | None | VPC configuration for the host. JSON: `{"VpcId":"string","SubnetIds":["string"],"SecurityGroupIds":["string"],"TlsCertificate":"string"}` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "HostArn": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 2.2 `delete-host`

Deletes a host resource.

**Synopsis:**
```bash
aws codestar-connections delete-host \
    --host-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--host-arn` | **Yes** | string | -- | ARN of the host to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `get-host`

Returns the details of a host.

**Synopsis:**
```bash
aws codestar-connections get-host \
    --host-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--host-arn` | **Yes** | string | -- | ARN of the host |

**Output Schema:**
```json
{
    "Name": "string",
    "Status": "PENDING|AVAILABLE|ERROR|VPC_CONFIG_DELETING",
    "ProviderType": "GitHubEnterpriseServer|GitLabSelfManaged",
    "ProviderEndpoint": "string",
    "VpcConfiguration": {
        "VpcId": "string",
        "SubnetIds": ["string"],
        "SecurityGroupIds": ["string"],
        "TlsCertificate": "string"
    }
}
```

---

### 2.4 `list-hosts`

Lists hosts in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-connections list-hosts \
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
    "Hosts": [
        {
            "Name": "string",
            "HostArn": "string",
            "ProviderType": "GitHubEnterpriseServer|GitLabSelfManaged",
            "ProviderEndpoint": "string",
            "VpcConfiguration": {
                "VpcId": "string",
                "SubnetIds": ["string"],
                "SecurityGroupIds": ["string"],
                "TlsCertificate": "string"
            },
            "Status": "PENDING|AVAILABLE|ERROR|VPC_CONFIG_DELETING",
            "StatusMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-host`

Updates a host's provider endpoint and VPC configuration.

**Synopsis:**
```bash
aws codestar-connections update-host \
    --host-arn <value> \
    [--provider-endpoint <value>] \
    [--vpc-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--host-arn` | **Yes** | string | -- | ARN of the host to update |
| `--provider-endpoint` | No | string | None | New URL endpoint of the installed provider |
| `--vpc-configuration` | No | structure | None | Updated VPC configuration |

**Output Schema:**
```json
{}
```
