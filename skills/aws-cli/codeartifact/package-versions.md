# Package Versions

### 4.1 `describe-package-version`

Returns detailed information about a package version.

**Synopsis:**
```bash
aws codeartifact describe-package-version \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --package-version <value> \
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
| `--package-version` | **Yes** | string | -- | Version of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |

**Output Schema:**
```json
{
    "packageVersion": {
        "format": "string",
        "namespace": "string",
        "packageName": "string",
        "displayName": "string",
        "version": "string",
        "summary": "string",
        "homePage": "string",
        "sourceCodeRepository": "string",
        "publishedTime": "timestamp",
        "licenses": [
            {
                "name": "string",
                "url": "string"
            }
        ],
        "revision": "string",
        "status": "Published|Unfinished|Unlisted|Archived|Disposed|Deleted",
        "origin": {
            "domainEntryPoint": {
                "repositoryName": "string",
                "externalConnectionName": "string"
            },
            "originType": "INTERNAL|EXTERNAL|UNKNOWN"
        }
    }
}
```

---

### 4.2 `list-package-versions`

Returns a list of versions for a package. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-package-versions \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--status <value>] \
    [--sort-by <value>] \
    [--origin-type <value>] \
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
| `--format` | **Yes** | string | -- | Package format |
| `--package` | **Yes** | string | -- | Name of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--status` | No | string | None | Filter by status: `Published`, `Unfinished`, `Unlisted`, `Archived`, `Disposed`, `Deleted` |
| `--sort-by` | No | string | None | Sort order: `PUBLISHED_TIME` |
| `--origin-type` | No | string | None | Filter by origin: `INTERNAL`, `EXTERNAL`, `UNKNOWN` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "defaultDisplayVersion": "string",
    "format": "string",
    "namespace": "string",
    "package": "string",
    "versions": [
        {
            "version": "string",
            "revision": "string",
            "status": "Published|Unfinished|Unlisted|Archived|Disposed|Deleted",
            "origin": {
                "domainEntryPoint": {
                    "repositoryName": "string",
                    "externalConnectionName": "string"
                },
                "originType": "INTERNAL|EXTERNAL|UNKNOWN"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.3 `list-package-version-assets`

Returns a list of assets for a specific package version. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-package-version-assets \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --package-version <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
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
| `--format` | **Yes** | string | -- | Package format |
| `--package` | **Yes** | string | -- | Name of the package |
| `--package-version` | **Yes** | string | -- | Version of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "format": "string",
    "namespace": "string",
    "package": "string",
    "version": "string",
    "versionRevision": "string",
    "assets": [
        {
            "name": "string",
            "size": "long",
            "hashes": {
                "MD5": "string",
                "SHA-1": "string",
                "SHA-256": "string",
                "SHA-512": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `list-package-version-dependencies`

Returns the dependencies of a package version.

**Synopsis:**
```bash
aws codeartifact list-package-version-dependencies \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --package-version <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--next-token <value>] \
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
| `--package-version` | **Yes** | string | -- | Version of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "format": "string",
    "namespace": "string",
    "package": "string",
    "version": "string",
    "versionRevision": "string",
    "dependencies": [
        {
            "namespace": "string",
            "package": "string",
            "dependencyType": "string",
            "versionRequirement": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `get-package-version-readme`

Returns the readme content for a package version, if available.

**Synopsis:**
```bash
aws codeartifact get-package-version-readme \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --package-version <value> \
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
| `--package-version` | **Yes** | string | -- | Version of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |

**Output Schema:**
```json
{
    "format": "string",
    "namespace": "string",
    "package": "string",
    "version": "string",
    "versionRevision": "string",
    "readme": "string"
}
```

---

### 4.6 `get-package-version-asset`

Returns the contents of an asset that is in a package version. The output is written to the specified file.

**Synopsis:**
```bash
aws codeartifact get-package-version-asset \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --package-version <value> \
    --asset <value> \
    <outfile> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--package-version-revision <value>] \
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
| `--package-version` | **Yes** | string | -- | Version of the package |
| `--asset` | **Yes** | string | -- | Name of the asset to retrieve |
| `outfile` | **Yes** | string | -- | Local file path to write the asset content |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--package-version-revision` | No | string | None | Specific revision of the package version |

**Output Schema:**
```json
{
    "assetName": "string",
    "packageVersion": "string",
    "packageVersionRevision": "string"
}
```

---

### 4.7 `copy-package-versions`

Copies package versions from one repository to another in the same domain.

**Synopsis:**
```bash
aws codeartifact copy-package-versions \
    --domain <value> \
    --source-repository <value> \
    --destination-repository <value> \
    --format <value> \
    --package <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--versions <value>] \
    [--version-revisions <value>] \
    [--allow-overwrite | --no-allow-overwrite] \
    [--include-from-upstream | --no-include-from-upstream] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--source-repository` | **Yes** | string | -- | Source repository name |
| `--destination-repository` | **Yes** | string | -- | Destination repository name |
| `--format` | **Yes** | string | -- | Package format |
| `--package` | **Yes** | string | -- | Name of the package |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--versions` | No | list(string) | None | Specific versions to copy |
| `--version-revisions` | No | map | None | Map of version to revision for optimistic locking |
| `--allow-overwrite` | No | boolean | false | Allow overwriting existing versions in destination |
| `--include-from-upstream` | No | boolean | true | Include versions from upstream repositories |

**Output Schema:**
```json
{
    "successfulVersions": {
        "version-string": {
            "revision": "string",
            "status": "Published|Unfinished|Unlisted|Archived|Disposed|Deleted"
        }
    },
    "failedVersions": {
        "version-string": {
            "errorCode": "ALREADY_EXISTS|MISMATCHED_REVISION|MISMATCHED_STATUS|NOT_ALLOWED|NOT_FOUND|SKIPPED",
            "errorMessage": "string"
        }
    }
}
```

---

### 4.8 `delete-package-versions`

Deletes one or more package versions from a repository.

**Synopsis:**
```bash
aws codeartifact delete-package-versions \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --versions <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--expected-status <value>] \
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
| `--versions` | **Yes** | list(string) | -- | Versions to delete |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--expected-status` | No | string | None | Expected current status of versions for validation |

**Output Schema:**
```json
{
    "successfulVersions": {
        "version-string": {
            "revision": "string",
            "status": "Deleted"
        }
    },
    "failedVersions": {
        "version-string": {
            "errorCode": "ALREADY_EXISTS|MISMATCHED_REVISION|MISMATCHED_STATUS|NOT_ALLOWED|NOT_FOUND|SKIPPED",
            "errorMessage": "string"
        }
    }
}
```

---

### 4.9 `dispose-package-versions`

Deletes the assets in provided package versions and sets the status to `Disposed`. A disposed version cannot be restored.

**Synopsis:**
```bash
aws codeartifact dispose-package-versions \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --versions <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--version-revisions <value>] \
    [--expected-status <value>] \
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
| `--versions` | **Yes** | list(string) | -- | Versions to dispose |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--version-revisions` | No | map | None | Map of version to revision for optimistic locking |
| `--expected-status` | No | string | None | Expected current status for validation |

**Output Schema:**
```json
{
    "successfulVersions": {
        "version-string": {
            "revision": "string",
            "status": "Disposed"
        }
    },
    "failedVersions": {
        "version-string": {
            "errorCode": "string",
            "errorMessage": "string"
        }
    }
}
```

---

### 4.10 `update-package-versions-status`

Updates the status of one or more package versions.

**Synopsis:**
```bash
aws codeartifact update-package-versions-status \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --versions <value> \
    --target-status <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--version-revisions <value>] \
    [--expected-status <value>] \
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
| `--versions` | **Yes** | list(string) | -- | Versions to update |
| `--target-status` | **Yes** | string | -- | Target status: `Published`, `Unlisted`, `Archived` |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--version-revisions` | No | map | None | Map of version to revision for optimistic locking |
| `--expected-status` | No | string | None | Expected current status for validation |

**Output Schema:**
```json
{
    "successfulVersions": {
        "version-string": {
            "revision": "string",
            "status": "Published|Unlisted|Archived"
        }
    },
    "failedVersions": {
        "version-string": {
            "errorCode": "string",
            "errorMessage": "string"
        }
    }
}
```

---

### 4.11 `publish-package-version`

Creates a new package version containing one or more assets (or files). Only supports `generic` package format.

**Synopsis:**
```bash
aws codeartifact publish-package-version \
    --domain <value> \
    --repository <value> \
    --format <value> \
    --package <value> \
    --package-version <value> \
    --asset-content <value> \
    --asset-name <value> \
    --asset-sha256 <value> \
    [--domain-owner <value>] \
    [--namespace <value>] \
    [--unfinished | --no-unfinished] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--repository` | **Yes** | string | -- | Name of the repository |
| `--format` | **Yes** | string | -- | Package format (only `generic` supported) |
| `--package` | **Yes** | string | -- | Name of the package |
| `--package-version` | **Yes** | string | -- | Version to publish |
| `--asset-content` | **Yes** | blob | -- | Content of the asset (file path with `fileb://`) |
| `--asset-name` | **Yes** | string | -- | Name of the asset |
| `--asset-sha256` | **Yes** | string | -- | SHA-256 hash of the asset content |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--namespace` | No | string | None | Package namespace |
| `--unfinished` | No | boolean | false | Mark the version as unfinished (allows adding more assets) |

**Output Schema:**
```json
{
    "format": "generic",
    "namespace": "string",
    "package": "string",
    "version": "string",
    "versionRevision": "string",
    "status": "Published|Unfinished",
    "asset": {
        "name": "string",
        "size": "long",
        "hashes": {
            "MD5": "string",
            "SHA-1": "string",
            "SHA-256": "string",
            "SHA-512": "string"
        }
    }
}
```

---

### 4.12 `get-authorization-token`

Generates a temporary authorization token for accessing repositories in a domain. The token can be used with package managers.

**Synopsis:**
```bash
aws codeartifact get-authorization-token \
    --domain <value> \
    [--domain-owner <value>] \
    [--duration-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--duration-seconds` | No | long | 43200 (12h) | Token duration in seconds (min 900, max 43200) |

**Output Schema:**
```json
{
    "authorizationToken": "string",
    "expiration": "timestamp"
}
```
