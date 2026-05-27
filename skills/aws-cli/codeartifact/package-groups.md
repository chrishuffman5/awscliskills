# Package Groups

### 5.1 `create-package-group`

Creates a package group in a domain. Package groups enable centralized origin configuration for packages that match a pattern.

**Synopsis:**
```bash
aws codeartifact create-package-group \
    --domain <value> \
    --package-group <value> \
    [--domain-owner <value>] \
    [--contact-info <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--package-group` | **Yes** | string | -- | Package group pattern (e.g., `npm//my-scope/*`, `/`) |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--contact-info` | No | string | None | Contact information for the package group |
| `--description` | No | string | None | Description of the package group |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

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
    }
}
```

---

### 5.2 `delete-package-group`

Deletes a package group from a domain.

**Synopsis:**
```bash
aws codeartifact delete-package-group \
    --domain <value> \
    --package-group <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--package-group` | **Yes** | string | -- | Pattern of the package group to delete |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

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
                    "mode": "string",
                    "effectiveMode": "string",
                    "inheritedFrom": {},
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
        "parent": {}
    }
}
```

---

### 5.3 `describe-package-group`

Returns a description of a package group.

**Synopsis:**
```bash
aws codeartifact describe-package-group \
    --domain <value> \
    --package-group <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--package-group` | **Yes** | string | -- | Pattern of the package group |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

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
    }
}
```

---

### 5.4 `list-package-groups`

Returns a list of package groups in a domain. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-package-groups \
    --domain <value> \
    [--domain-owner <value>] \
    [--prefix <value>] \
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
| `--prefix` | No | string | None | Filter by pattern prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "packageGroups": [
        {
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
                        "mode": "string",
                        "effectiveMode": "string",
                        "inheritedFrom": {},
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
            "parent": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `update-package-group`

Updates description and contact information of a package group.

**Synopsis:**
```bash
aws codeartifact update-package-group \
    --domain <value> \
    --package-group <value> \
    [--domain-owner <value>] \
    [--contact-info <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--package-group` | **Yes** | string | -- | Pattern of the package group |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--contact-info` | No | string | None | Updated contact information |
| `--description` | No | string | None | Updated description |

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
        "originConfiguration": {},
        "parent": {}
    }
}
```

---

### 5.6 `update-package-group-origin-configuration`

Updates the origin configuration for a package group, controlling publish and upstream restrictions.

**Synopsis:**
```bash
aws codeartifact update-package-group-origin-configuration \
    --domain <value> \
    --package-group <value> \
    [--domain-owner <value>] \
    [--restrictions <value>] \
    [--add-allowed-repositories <value>] \
    [--remove-allowed-repositories <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--package-group` | **Yes** | string | -- | Pattern of the package group |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--restrictions` | No | map | None | Origin restrictions. JSON: `{"publish":{"restrictionMode":"ALLOW|BLOCK|ALLOW_SPECIFIC_REPOSITORIES|INHERIT"},"upstream":{"restrictionMode":"..."}}` |
| `--add-allowed-repositories` | No | list | None | Repositories to add to the allowed list. Shorthand: `repositoryName=string,originRestrictionType=PUBLISH\|UPSTREAM ...` |
| `--remove-allowed-repositories` | No | list | None | Repositories to remove from the allowed list |

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
                    "effectiveMode": "string",
                    "inheritedFrom": {},
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
        "parent": {}
    },
    "allowedRepositoryUpdates": {
        "PUBLISH": {
            "ADDED": ["string"],
            "REMOVED": ["string"]
        },
        "UPSTREAM": {
            "ADDED": ["string"],
            "REMOVED": ["string"]
        }
    }
}
```

---

### 5.7 `list-allowed-repositories-for-group`

Returns a list of repositories allowed for a specific origin restriction type on a package group. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-allowed-repositories-for-group \
    --domain <value> \
    --package-group <value> \
    --origin-restriction-type <value> \
    [--domain-owner <value>] \
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
| `--package-group` | **Yes** | string | -- | Pattern of the package group |
| `--origin-restriction-type` | **Yes** | string | -- | Origin restriction type: `PUBLISH`, `UPSTREAM` |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "allowedRepositories": ["string"],
    "nextToken": "string"
}
```

---

### 5.8 `list-associated-packages`

Returns a list of packages associated with a package group. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-associated-packages \
    --domain <value> \
    --package-group <value> \
    [--domain-owner <value>] \
    [--preview | --no-preview] \
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
| `--package-group` | **Yes** | string | -- | Pattern of the package group |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--preview` | No | boolean | false | Preview which packages would be associated |
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
            "associationType": "STRONG|WEAK"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.9 `list-sub-package-groups`

Returns a list of direct child package groups for a given package group. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-sub-package-groups \
    --domain <value> \
    --package-group <value> \
    [--domain-owner <value>] \
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
| `--package-group` | **Yes** | string | -- | Pattern of the parent package group |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "packageGroups": [
        {
            "arn": "string",
            "pattern": "string",
            "domainName": "string",
            "domainOwner": "string",
            "createdTime": "timestamp",
            "contactInfo": "string",
            "description": "string",
            "originConfiguration": {},
            "parent": {}
        }
    ],
    "nextToken": "string"
}
```
