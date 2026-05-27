# Branches

### 2.1 `create-branch`

Creates a new branch in a repository.

**Synopsis:**
```bash
aws codecommit create-branch \
    --repository-name <value> \
    --branch-name <value> \
    --commit-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--branch-name` | **Yes** | string | -- | Name for the new branch |
| `--commit-id` | **Yes** | string | -- | Commit ID to point the branch to |

**Output Schema:**
```json
{}
```

---

### 2.2 `delete-branch`

Deletes a branch from a repository. Cannot delete the default branch.

**Synopsis:**
```bash
aws codecommit delete-branch \
    --repository-name <value> \
    --branch-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--branch-name` | **Yes** | string | -- | Name of the branch to delete |

**Output Schema:**
```json
{
    "deletedBranch": {
        "branchName": "string",
        "commitId": "string"
    }
}
```

---

### 2.3 `get-branch`

Returns information about a branch, including the last commit ID.

**Synopsis:**
```bash
aws codecommit get-branch \
    [--repository-name <value>] \
    [--branch-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | No | string | -- | Name of the repository |
| `--branch-name` | No | string | -- | Name of the branch |

**Output Schema:**
```json
{
    "branch": {
        "branchName": "string",
        "commitId": "string"
    }
}
```

---

### 2.4 `list-branches`

Lists all branches in a repository. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit list-branches \
    --repository-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "branches": ["string"],
    "nextToken": "string"
}
```

---

### 2.5 `update-default-branch`

Sets or changes the default branch for a repository.

**Synopsis:**
```bash
aws codecommit update-default-branch \
    --repository-name <value> \
    --default-branch-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--default-branch-name` | **Yes** | string | -- | Name of the new default branch |

**Output Schema:**
```json
{}
```
