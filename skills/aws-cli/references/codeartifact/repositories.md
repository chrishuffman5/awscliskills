# Repositories

### 2.1 `create-repository`

Creates a new repository in a domain.

**Synopsis:**
```bash
aws codeartifact create-repository \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--description <value>] \
    [--upstreams <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain that contains the repository |
| `--repository` | **Yes** | string | -- | Name of the repository to create (2-100 chars: letters, numbers, hyphens, underscores, dots) |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--description` | No | string | None | Description of the repository |
| `--upstreams` | No | list | None | Upstream repositories. Shorthand: `repositoryName=string ...` |
| `--tags` | No | list | None | Tags to associate. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "repository": {
        "name": "string",
        "administratorAccount": "string",
        "domainName": "string",
        "domainOwner": "string",
        "arn": "string",
        "description": "string",
        "upstreams": [
            {
                "repositoryName": "string"
            }
        ],
        "externalConnections": [
            {
                "externalConnectionName": "string",
                "packageFormat": "npm|pypi|maven|nuget|generic|swift|cargo|ruby",
                "status": "Available"
            }
        ],
        "createdTime": "timestamp"
    }
}
```

---

### 2.2 `delete-repository`

Deletes a repository.

**Synopsis:**
```bash
aws codeartifact delete-repository \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository to delete |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "repository": {
        "name": "string",
        "administratorAccount": "string",
        "domainName": "string",
        "domainOwner": "string",
        "arn": "string",
        "description": "string",
        "upstreams": [],
        "externalConnections": [],
        "createdTime": "timestamp"
    }
}
```

---

### 2.3 `describe-repository`

Returns a repository description.

**Synopsis:**
```bash
aws codeartifact describe-repository \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "repository": {
        "name": "string",
        "administratorAccount": "string",
        "domainName": "string",
        "domainOwner": "string",
        "arn": "string",
        "description": "string",
        "upstreams": [
            {
                "repositoryName": "string"
            }
        ],
        "externalConnections": [
            {
                "externalConnectionName": "string",
                "packageFormat": "string",
                "status": "Available"
            }
        ],
        "createdTime": "timestamp"
    }
}
```

---

### 2.4 `list-repositories`

Returns a list of repositories in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-repositories \
    [--repository-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-prefix` | No | string | None | Filter repositories by name prefix |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "repositories": [
        {
            "name": "string",
            "administratorAccount": "string",
            "domainName": "string",
            "domainOwner": "string",
            "arn": "string",
            "description": "string",
            "createdTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `list-repositories-in-domain`

Returns a list of repositories in a domain. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-repositories-in-domain \
    --domain <value> \
    [--domain-owner <value>] \
    [--administrator-account <value>] \
    [--repository-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--administrator-account` | No | string | None | Filter by administrator account |
| `--repository-prefix` | No | string | None | Filter by name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "repositories": [
        {
            "name": "string",
            "administratorAccount": "string",
            "domainName": "string",
            "domainOwner": "string",
            "arn": "string",
            "description": "string",
            "createdTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.6 `update-repository`

Updates the description or upstream repositories for a repository.

**Synopsis:**
```bash
aws codeartifact update-repository \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--description <value>] \
    [--upstreams <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository to update |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--description` | No | string | None | Updated description |
| `--upstreams` | No | list | None | Updated upstream repositories. Shorthand: `repositoryName=string ...` |

**Output Schema:**
```json
{
    "repository": {
        "name": "string",
        "administratorAccount": "string",
        "domainName": "string",
        "domainOwner": "string",
        "arn": "string",
        "description": "string",
        "upstreams": [
            {
                "repositoryName": "string"
            }
        ],
        "externalConnections": [],
        "createdTime": "timestamp"
    }
}
```

---

### 2.7 `get-repository-endpoint`

Returns the endpoint of a repository for a specific package format.

**Synopsis:**
```bash
aws codeartifact get-repository-endpoint \
    --domain <value> \
    --repository <value> \
    --format <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--format` | **Yes** | string | -- | Package format: `npm`, `pypi`, `maven`, `nuget`, `generic`, `swift`, `cargo`, `ruby` |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "repositoryEndpoint": "string"
}
```

---

### 2.8 `get-repository-permissions-policy`

Returns the resource policy set on a repository.

**Synopsis:**
```bash
aws codeartifact get-repository-permissions-policy \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "policy": {
        "resourceArn": "string",
        "revision": "string",
        "document": "string"
    }
}
```

---

### 2.9 `put-repository-permissions-policy`

Sets the resource policy on a repository.

**Synopsis:**
```bash
aws codeartifact put-repository-permissions-policy \
    --domain <value> \
    --repository <value> \
    --policy-document <value> \
    [--domain-owner <value>] \
    [--policy-revision <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--policy-document` | **Yes** | string | -- | JSON policy document or `file://` path |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--policy-revision` | No | string | None | Current policy revision for optimistic locking |

**Output Schema:**
```json
{
    "policy": {
        "resourceArn": "string",
        "revision": "string",
        "document": "string"
    }
}
```

---

### 2.10 `delete-repository-permissions-policy`

Deletes the resource policy set on a repository.

**Synopsis:**
```bash
aws codeartifact delete-repository-permissions-policy \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--policy-revision <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--policy-revision` | No | string | None | Current policy revision for optimistic locking |

**Output Schema:**
```json
{
    "policy": {
        "resourceArn": "string",
        "revision": "string",
        "document": "string"
    }
}
```

---

### 2.11 `associate-external-connection`

Adds an existing external connection to a repository. Each repository can have one external connection per package format.

**Synopsis:**
```bash
aws codeartifact associate-external-connection \
    --domain <value> \
    --repository <value> \
    --external-connection <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--external-connection` | **Yes** | string | -- | External connection name (e.g., `public:npmjs`, `public:pypi`, `public:maven-central`) |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "repository": {
        "name": "string",
        "administratorAccount": "string",
        "domainName": "string",
        "domainOwner": "string",
        "arn": "string",
        "description": "string",
        "upstreams": [],
        "externalConnections": [
            {
                "externalConnectionName": "string",
                "packageFormat": "npm|pypi|maven|nuget|generic|swift|cargo|ruby",
                "status": "Available"
            }
        ],
        "createdTime": "timestamp"
    }
}
```

---

### 2.12 `disassociate-external-connection`

Removes an existing external connection from a repository.

**Synopsis:**
```bash
aws codeartifact disassociate-external-connection \
    --domain <value> \
    --repository <value> \
    --external-connection <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--external-connection` | **Yes** | string | -- | External connection name to remove |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "repository": {
        "name": "string",
        "administratorAccount": "string",
        "domainName": "string",
        "domainOwner": "string",
        "arn": "string",
        "description": "string",
        "upstreams": [],
        "externalConnections": [],
        "createdTime": "timestamp"
    }
}
```

---

### 2.13 `login`

Configures a package manager client (npm, pip, twine, dotnet, swift, cargo) to use a CodeArtifact repository. Sets up authentication credentials and endpoint configuration.

**Synopsis:**
```bash
aws codeartifact login \
    --tool <value> \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--duration-seconds <value>] \
    [--dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tool` | **Yes** | string | -- | Package manager tool: `npm`, `pip`, `twine`, `dotnet`, `swift`, `nuget`, `cargo` |
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Scope/namespace for the login (e.g., npm scope) |
| `--duration-seconds` | No | integer | 43200 (12h) | Token duration in seconds (min 900, max 43200) |
| `--dry-run` | No | boolean | false | Print configuration commands without executing them |

**Output:** Configures the specified tool and prints configuration status to stdout. No JSON output.
