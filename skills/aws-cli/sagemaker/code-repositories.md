# Code Repositories

## 1. `create-code-repository`

Creates a Git repository as a resource in SageMaker for use with notebook instances.

**Synopsis:**
```bash
aws sagemaker create-code-repository \
    --code-repository-name <value> \
    --git-config <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-repository-name` | **Yes** | string | -- | Repository name (1-63 chars, `[a-zA-Z0-9](-*[a-zA-Z0-9])*`) |
| `--git-config` | **Yes** | structure | -- | Git configuration |
| `--tags` | No | list | -- | Key-value tags |

**Git Config:**
```json
{
    "RepositoryUrl": "string",
    "Branch": "string",
    "SecretArn": "string"
}
```

**Output Schema:**
```json
{
    "CodeRepositoryArn": "string"
}
```

---

## 2. `describe-code-repository`

Returns details about a code repository.

```bash
aws sagemaker describe-code-repository --code-repository-name <value>
```

**Output Schema:**
```json
{
    "CodeRepositoryName": "string",
    "CodeRepositoryArn": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "GitConfig": {
        "RepositoryUrl": "string",
        "Branch": "string",
        "SecretArn": "string"
    }
}
```

---

## 3. `list-code-repositories`

Lists code repositories. **Paginated operation.**

```bash
aws sagemaker list-code-repositories \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-contains` | No | string | -- | Filter by name substring |
| `--sort-by` | No | string | `Name` | `Name`, `CreationTime`, `LastModifiedTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "CodeRepositorySummaryList": [
        {
            "CodeRepositoryName": "string",
            "CodeRepositoryArn": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "GitConfig": {"RepositoryUrl": "string", "Branch": "string", "SecretArn": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `update-code-repository`

Updates a code repository (Git config only).

```bash
aws sagemaker update-code-repository \
    --code-repository-name <value> \
    [--git-config <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-repository-name` | **Yes** | string | -- | Repository name |
| `--git-config` | No | structure | -- | Updated `SecretArn` (only field that can be updated) |

**Output Schema:**
```json
{
    "CodeRepositoryArn": "string"
}
```

---

## 5. `delete-code-repository`

Deletes a code repository.

```bash
aws sagemaker delete-code-repository --code-repository-name <value>
```

**Output:** None
