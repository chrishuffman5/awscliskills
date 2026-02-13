# Packages

### 3.1 `describe-package`

Returns a description of a package in a repository.

**Synopsis:**
```bash
aws codeartifact describe-package \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--format` | **Yes** | string | -- | Package format: `npm`, `pypi`, `maven`, `nuget`, `generic`, `swift`, `cargo`, `ruby` |
| `--package` | **Yes** | string | -- | Name of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace (e.g., Maven groupId, npm scope) |

**Output Schema:**
```json
{
    "package": {
        "format": "npm|pypi|maven|nuget|generic|swift|cargo|ruby",
        "namespace": "string",
        "name": "string",
        "originConfiguration": {
            "restrictions": {
                "publish": "ALLOW|BLOCK",
                "upstream": "ALLOW|BLOCK"
            }
        }
    }
}
```

---

### 3.2 `list-packages`

Returns a list of packages in a repository. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-packages \
    --domain <value> \
    --repository <value> \
    [--domain-owner <value>] \
    [--format <value>] \
    [--namespace <value>] \
    [--package-prefix <value>] \
    [--publish <value>] \
    [--upstream <value>] \
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
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--format` | No | string | None | Filter by package format |
| `--namespace` | No | string | None | Filter by namespace |
| `--package-prefix` | No | string | None | Filter by package name prefix |
| `--publish` | No | string | None | Filter by publish origin restriction: `ALLOW`, `BLOCK` |
| `--upstream` | No | string | None | Filter by upstream origin restriction: `ALLOW`, `BLOCK` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "packages": [
        {
            "format": "npm|pypi|maven|nuget|generic|swift|cargo|ruby",
            "namespace": "string",
            "package": "string",
            "originConfiguration": {
                "restrictions": {
                    "publish": "ALLOW|BLOCK",
                    "upstream": "ALLOW|BLOCK"
                }
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 3.3 `delete-package`

Deletes a package and all associated package versions.

**Synopsis:**
```bash
aws codeartifact delete-package \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--format` | **Yes** | string | -- | Package format |
| `--package` | **Yes** | string | -- | Name of the package to delete |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |

**Output Schema:**
```json
{
    "deletedPackage": {
        "format": "npm|pypi|maven|nuget|generic|swift|cargo|ruby",
        "namespace": "string",
        "package": "string",
        "originConfiguration": {
            "restrictions": {
                "publish": "ALLOW|BLOCK",
                "upstream": "ALLOW|BLOCK"
            }
        }
    }
}
```

---

### 3.4 `get-associated-package-group`

Returns the most closely associated package group to the specified package.

**Synopsis:**
```bash
aws codeartifact get-associated-package-group \
    --domain <value> \
    --format <value> \
    --package <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--format` | **Yes** | string | -- | Package format |
| `--package` | **Yes** | string | -- | Name of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |

**Output Schema:**
```json
{
    "packageGroup": {
        "arn": "string",
        "pattern": "string",
        "domainName": "string",
        "domainOwner": "string",
        "createdTime": "timestamp",
        "contactInfo": "string",
        "description": "string",
        "originConfiguration": {
            "restrictions": {
                "publish": {
                    "mode": "ALLOW|BLOCK|ALLOW_SPECIFIC_REPOSITORIES|INHERIT",
                    "effectiveMode": "ALLOW|BLOCK|ALLOW_SPECIFIC_REPOSITORIES|INHERIT",
                    "inheritedFrom": {
                        "arn": "string",
                        "pattern": "string"
                    },
                    "repositoryCount": "long"
                },
                "upstream": {
                    "mode": "string",
                    "effectiveMode": "string",
                    "inheritedFrom": {},
                    "repositoryCount": "long"
                }
            }
        },
        "parent": {
            "arn": "string",
            "pattern": "string"
        }
    },
    "associationType": "STRONG|WEAK"
}
```

---

### 3.5 `put-package-origin-configuration`

Sets the origin configuration for a package, controlling whether it can be published directly or fetched from upstream.

**Synopsis:**
```bash
aws codeartifact put-package-origin-configuration \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --restrictions <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--format` | **Yes** | string | -- | Package format |
| `--package` | **Yes** | string | -- | Name of the package |
| `--restrictions` | **Yes** | structure | -- | Origin restrictions. Shorthand: `publish=ALLOW\|BLOCK,upstream=ALLOW\|BLOCK` |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |

**Output Schema:**
```json
{
    "originConfiguration": {
        "restrictions": {
            "publish": "ALLOW|BLOCK",
            "upstream": "ALLOW|BLOCK"
        }
    }
}
```
