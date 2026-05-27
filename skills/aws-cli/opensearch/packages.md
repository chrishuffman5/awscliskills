# Packages

### 3.1 `create-package`

Creates a package for use with OpenSearch Service domains. Packages contain plugins, dictionaries, or other custom resources.

**Synopsis:**
```bash
aws opensearch create-package \
    --package-name <value> \
    --package-type <value> \
    --package-source <value> \
    [--package-description <value>] \
    [--package-configuration <value>] \
    [--engine-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name (3-28 chars, pattern: `[a-z][a-z0-9\-]+`) |
| `--package-type` | **Yes** | string | -- | `TXT-DICTIONARY`, `ZIP-PLUGIN` |
| `--package-source` | **Yes** | structure | -- | S3 source. Shorthand: `S3BucketName=string,S3Key=string` |
| `--package-description` | No | string | None | Description (0-1024 chars) |
| `--package-configuration` | No | structure | None | Package configuration |
| `--engine-version` | No | string | None | Required engine version |

**Output Schema:**
```json
{
    "PackageDetails": {
        "PackageID": "string",
        "PackageName": "string",
        "PackageType": "TXT-DICTIONARY|ZIP-PLUGIN",
        "PackageDescription": "string",
        "PackageStatus": "COPYING|COPY_FAILED|VALIDATING|VALIDATION_FAILED|AVAILABLE|DELETING|DELETED|DELETE_FAILED",
        "CreatedAt": "timestamp",
        "LastUpdatedAt": "timestamp",
        "AvailablePackageVersion": "string",
        "EngineVersion": "string"
    }
}
```

---

### 3.2 `delete-package`

Deletes a package.

**Synopsis:**
```bash
aws opensearch delete-package \
    --package-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-id` | **Yes** | string | -- | Package ID to delete |

**Output Schema:**
```json
{
    "PackageDetails": {
        "PackageID": "string",
        "PackageName": "string",
        "PackageStatus": "DELETING"
    }
}
```

---

### 3.3 `update-package`

Updates an existing package with a new version.

**Synopsis:**
```bash
aws opensearch update-package \
    --package-id <value> \
    --package-source <value> \
    [--package-description <value>] \
    [--commit-message <value>] \
    [--package-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-id` | **Yes** | string | -- | Package ID to update |
| `--package-source` | **Yes** | structure | -- | S3 source. Shorthand: `S3BucketName=string,S3Key=string` |
| `--package-description` | No | string | None | Updated description |
| `--commit-message` | No | string | None | Commit message for version |
| `--package-configuration` | No | structure | None | Updated configuration |

**Output Schema:**
```json
{
    "PackageDetails": {
        "PackageID": "string",
        "PackageName": "string",
        "PackageStatus": "string",
        "AvailablePackageVersion": "string"
    }
}
```

---

### 3.4 `describe-packages`

Lists packages. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch describe-packages \
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
| `--filters` | No | list | None | Filters. Shorthand: `Name=PackageID\|PackageName\|PackageStatus\|PackageType\|EngineVersion,Value=string ...` |

**Output Schema:**
```json
{
    "PackageDetailsList": [
        {
            "PackageID": "string",
            "PackageName": "string",
            "PackageType": "string",
            "PackageDescription": "string",
            "PackageStatus": "string",
            "CreatedAt": "timestamp",
            "AvailablePackageVersion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `associate-package`

Associates a package with a domain.

**Synopsis:**
```bash
aws opensearch associate-package \
    --package-id <value> \
    --domain-name <value> \
    [--prerequisite-package-id-list <value>] \
    [--association-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-id` | **Yes** | string | -- | Package ID to associate |
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--prerequisite-package-id-list` | No | list(string) | None | Prerequisite package IDs |
| `--association-configuration` | No | structure | None | Association config |

**Output Schema:**
```json
{
    "DomainPackageDetails": {
        "PackageID": "string",
        "PackageName": "string",
        "PackageType": "string",
        "DomainName": "string",
        "DomainPackageStatus": "ASSOCIATING|ASSOCIATION_FAILED|ACTIVE|DISSOCIATING|DISSOCIATION_FAILED",
        "PackageVersion": "string"
    }
}
```

---

### 3.6 `dissociate-package`

Dissociates a package from a domain.

**Synopsis:**
```bash
aws opensearch dissociate-package \
    --package-id <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-id` | **Yes** | string | -- | Package ID |
| `--domain-name` | **Yes** | string | -- | Domain name |

**Output Schema:**
```json
{
    "DomainPackageDetails": {
        "PackageID": "string",
        "DomainName": "string",
        "DomainPackageStatus": "DISSOCIATING"
    }
}
```

---

### 3.7 `get-package-version-history`

Returns version history for a package. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch get-package-version-history \
    --package-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-id` | **Yes** | string | -- | Package ID |

**Output Schema:**
```json
{
    "PackageID": "string",
    "PackageVersionHistoryList": [
        {
            "PackageVersion": "string",
            "CommitMessage": "string",
            "CreatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.8 `list-domains-for-package`

Lists domains that have a specific package associated. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch list-domains-for-package \
    --package-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-id` | **Yes** | string | -- | Package ID |

**Output Schema:**
```json
{
    "DomainPackageDetailsList": [
        {
            "PackageID": "string",
            "DomainName": "string",
            "DomainPackageStatus": "string",
            "PackageVersion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.9 `list-packages-for-domain`

Lists packages associated with a domain. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch list-packages-for-domain \
    --domain-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |

**Output Schema:**
```json
{
    "DomainPackageDetailsList": [
        {
            "PackageID": "string",
            "PackageName": "string",
            "PackageType": "string",
            "DomainName": "string",
            "DomainPackageStatus": "string",
            "PackageVersion": "string"
        }
    ],
    "NextToken": "string"
}
```
