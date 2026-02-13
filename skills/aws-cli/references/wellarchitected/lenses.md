# Lenses

### 2.1 `import-lens`

Imports a custom lens from a JSON file or string.

**Synopsis:**
```bash
aws wellarchitected import-lens \
    --json-string <value> \
    --client-request-token <value> \
    [--lens-alias <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--json-string` | **Yes** | string | -- | Lens JSON definition (min 2, max 500000) |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |
| `--lens-alias` | No | string | None | Alias for existing lens (updates it) |
| `--tags` | No | map | None | Tags (1-50 tags) |

**Output Schema:**
```json
{
    "LensArn": "string",
    "Status": "IN_PROGRESS|COMPLETE|ERROR"
}
```

---

### 2.2 `export-lens`

Exports a custom lens as JSON.

**Synopsis:**
```bash
aws wellarchitected export-lens \
    --lens-alias <value> \
    [--lens-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--lens-version` | No | string | None | Specific version to export |

**Output Schema:**
```json
{
    "LensJSON": "string"
}
```

---

### 2.3 `delete-lens`

Deletes a custom lens. Cannot delete AWS official lenses.

**Synopsis:**
```bash
aws wellarchitected delete-lens \
    --lens-alias <value> \
    --client-request-token <value> \
    --lens-status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |
| `--lens-status` | **Yes** | string | -- | Status for deletion: `ALL` or `DRAFT` |

**Output Schema:**
```json
None
```

---

### 2.4 `get-lens`

Retrieves a lens by alias or ARN.

**Synopsis:**
```bash
aws wellarchitected get-lens \
    --lens-alias <value> \
    [--lens-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--lens-version` | No | string | None | Specific version |

**Output Schema:**
```json
{
    "Lens": {
        "LensArn": "string",
        "LensVersion": "string",
        "Name": "string",
        "Description": "string",
        "Owner": "string",
        "ShareInvitationId": "string",
        "Tags": {"string": "string"}
    }
}
```

---

### 2.5 `list-lenses`

Lists available lenses. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-lenses \
    [--lens-type <value>] \
    [--lens-status <value>] \
    [--lens-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-type` | No | string | None | `AWS_OFFICIAL`, `CUSTOM_SHARED`, or `CUSTOM_SELF` |
| `--lens-status` | No | string | None | `ALL`, `DRAFT`, or `PUBLISHED` |
| `--lens-name` | No | string | None | Filter by lens name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LensSummaries": [
        {
            "LensAlias": "string",
            "LensArn": "string",
            "LensVersion": "string",
            "LensName": "string",
            "LensType": "AWS_OFFICIAL|CUSTOM_SHARED|CUSTOM_SELF",
            "Description": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "LensStatus": "CURRENT|NOT_CURRENT|DEPRECATED|DELETED|UNSHARED",
            "Owner": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `create-lens-version`

Creates a new version of a custom lens.

**Synopsis:**
```bash
aws wellarchitected create-lens-version \
    --lens-alias <value> \
    --lens-version <value> \
    --client-request-token <value> \
    [--is-major-version | --no-is-major-version] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--lens-version` | **Yes** | string | -- | Version string (1-32 chars) |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |
| `--is-major-version` | No | boolean | false | Whether this is a major version |

**Output Schema:**
```json
{
    "LensArn": "string",
    "LensVersion": "string"
}
```

---

### 2.7 `get-lens-version-difference`

Gets the difference between two versions of a lens.

**Synopsis:**
```bash
aws wellarchitected get-lens-version-difference \
    --lens-alias <value> \
    [--base-lens-version <value>] \
    [--target-lens-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--base-lens-version` | No | string | None | Base version (omit for current) |
| `--target-lens-version` | No | string | None | Target version (omit for latest) |

**Output Schema:**
```json
{
    "LensAlias": "string",
    "LensArn": "string",
    "BaseLensVersion": "string",
    "TargetLensVersion": "string",
    "LatestLensVersion": "string",
    "VersionDifferences": {
        "PillarDifferences": [
            {
                "PillarId": "string",
                "PillarName": "string",
                "DifferenceStatus": "UPDATED|NEW|DELETED",
                "QuestionDifferences": [
                    {
                        "QuestionId": "string",
                        "QuestionTitle": "string",
                        "DifferenceStatus": "UPDATED|NEW|DELETED"
                    }
                ]
            }
        ]
    }
}
```

---

### 2.8 `associate-lenses`

Associates lenses with a workload.

**Synopsis:**
```bash
aws wellarchitected associate-lenses \
    --workload-id <value> \
    --lens-aliases <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-aliases` | **Yes** | list(string) | -- | Lens aliases or ARNs (min 1) |

**Output Schema:**
```json
None
```

---

### 2.9 `disassociate-lenses`

Removes lenses from a workload.

**Synopsis:**
```bash
aws wellarchitected disassociate-lenses \
    --workload-id <value> \
    --lens-aliases <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-aliases` | **Yes** | list(string) | -- | Lens aliases or ARNs to remove |

**Output Schema:**
```json
None
```

---

### 2.10 `create-lens-share`

Shares a custom lens with another account.

**Synopsis:**
```bash
aws wellarchitected create-lens-share \
    --lens-alias <value> \
    --shared-with <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--shared-with` | **Yes** | string | -- | Account ID, org ID, or OU ID |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "ShareId": "string"
}
```

---

### 2.11 `delete-lens-share`

Deletes a lens share.

**Synopsis:**
```bash
aws wellarchitected delete-lens-share \
    --share-id <value> \
    --lens-alias <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--share-id` | **Yes** | string | -- | Share ID |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
None
```

---

### 2.12 `list-lens-shares`

Lists shares for a lens. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-lens-shares \
    --lens-alias <value> \
    [--shared-with-prefix <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--shared-with-prefix` | No | string | None | Filter by shared-with prefix |
| `--status` | No | string | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LensShareSummaries": [
        {
            "ShareId": "string",
            "SharedWith": "string",
            "Status": "string",
            "StatusMessage": "string"
        }
    ],
    "NextToken": "string"
}
```
