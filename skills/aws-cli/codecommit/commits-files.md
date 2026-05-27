# Commits & Files

### 3.1 `create-commit`

Creates a commit for a repository on a specified branch, with file additions, modifications, and deletions.

**Synopsis:**
```bash
aws codecommit create-commit \
    --repository-name <value> \
    --branch-name <value> \
    [--parent-commit-id <value>] \
    [--author-name <value>] \
    [--email <value>] \
    [--commit-message <value>] \
    [--keep-empty-folders | --no-keep-empty-folders] \
    [--put-files <value>] \
    [--delete-files <value>] \
    [--set-file-modes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--branch-name` | **Yes** | string | -- | Name of the branch to commit to |
| `--parent-commit-id` | No | string | -- | Full commit ID of the parent (required unless creating first commit) |
| `--author-name` | No | string | -- | Name of the commit author |
| `--email` | No | string | -- | Email of the commit author |
| `--commit-message` | No | string | -- | Commit message |
| `--keep-empty-folders` | No | boolean | false | Keep empty folders in the commit |
| `--put-files` | No | list | -- | Files to add or update. JSON: `[{"filePath":"string","fileMode":"EXECUTABLE|NORMAL|SYMLINK","fileContent":"blob","sourceFile":{"filePath":"string","isMove":boolean}}]` |
| `--delete-files` | No | list | -- | Files to delete. Shorthand: `filePath=string ...` |
| `--set-file-modes` | No | list | -- | File modes to set. Shorthand: `filePath=string,fileMode=EXECUTABLE|NORMAL|SYMLINK ...` |

**Output Schema:**
```json
{
    "commitId": "string",
    "treeId": "string",
    "filesAdded": [
        {
            "absolutePath": "string",
            "blobId": "string",
            "fileMode": "EXECUTABLE|NORMAL|SYMLINK"
        }
    ],
    "filesUpdated": [
        {
            "absolutePath": "string",
            "blobId": "string",
            "fileMode": "EXECUTABLE|NORMAL|SYMLINK"
        }
    ],
    "filesDeleted": [
        {
            "absolutePath": "string",
            "blobId": "string",
            "fileMode": "EXECUTABLE|NORMAL|SYMLINK"
        }
    ]
}
```

---

### 3.2 `get-commit`

Returns information about a commit.

**Synopsis:**
```bash
aws codecommit get-commit \
    --repository-name <value> \
    --commit-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--commit-id` | **Yes** | string | -- | Full commit ID |

**Output Schema:**
```json
{
    "commit": {
        "commitId": "string",
        "treeId": "string",
        "parents": ["string"],
        "message": "string",
        "author": {
            "name": "string",
            "email": "string",
            "date": "string"
        },
        "committer": {
            "name": "string",
            "email": "string",
            "date": "string"
        },
        "additionalData": "string"
    }
}
```

---

### 3.3 `batch-get-commits`

Returns information about one or more commits.

**Synopsis:**
```bash
aws codecommit batch-get-commits \
    --commit-ids <value> \
    --repository-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--commit-ids` | **Yes** | list(string) | -- | Full commit IDs (max 25) |
| `--repository-name` | **Yes** | string | -- | Name of the repository |

**Output Schema:**
```json
{
    "commits": [
        {
            "commitId": "string",
            "treeId": "string",
            "parents": ["string"],
            "message": "string",
            "author": {
                "name": "string",
                "email": "string",
                "date": "string"
            },
            "committer": {
                "name": "string",
                "email": "string",
                "date": "string"
            },
            "additionalData": "string"
        }
    ],
    "errors": [
        {
            "commitId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 3.4 `get-differences`

Returns information about the differences in a valid commit specifier (branch, tag, HEAD, or commit ID). **Paginated operation.**

**Synopsis:**
```bash
aws codecommit get-differences \
    --repository-name <value> \
    --after-commit-specifier <value> \
    [--before-commit-specifier <value>] \
    [--before-path <value>] \
    [--after-path <value>] \
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
| `--after-commit-specifier` | **Yes** | string | -- | Commit specifier for the after comparison |
| `--before-commit-specifier` | No | string | -- | Commit specifier for the before comparison |
| `--before-path` | No | string | -- | File path to filter before differences |
| `--after-path` | No | string | -- | File path to filter after differences |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "differences": [
        {
            "beforeBlob": {
                "blobId": "string",
                "path": "string",
                "mode": "string"
            },
            "afterBlob": {
                "blobId": "string",
                "path": "string",
                "mode": "string"
            },
            "changeType": "A|M|D"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `get-blob`

Returns the base-64 encoded content of a blob object.

**Synopsis:**
```bash
aws codecommit get-blob \
    --repository-name <value> \
    --blob-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--blob-id` | **Yes** | string | -- | ID of the blob object |

**Output Schema:**
```json
{
    "content": "blob"
}
```

---

### 3.6 `get-file`

Returns the contents of a specified file in a repository.

**Synopsis:**
```bash
aws codecommit get-file \
    --repository-name <value> \
    --file-path <value> \
    [--commit-specifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--file-path` | **Yes** | string | -- | Full path to the file |
| `--commit-specifier` | No | string | HEAD | Branch, tag, or commit ID |

**Output Schema:**
```json
{
    "commitId": "string",
    "blobId": "string",
    "filePath": "string",
    "fileMode": "EXECUTABLE|NORMAL|SYMLINK",
    "fileSize": "long",
    "fileContent": "blob"
}
```

---

### 3.7 `get-folder`

Returns the contents of a folder in a repository.

**Synopsis:**
```bash
aws codecommit get-folder \
    --repository-name <value> \
    --folder-path <value> \
    [--commit-specifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--folder-path` | **Yes** | string | -- | Full path to the folder (use `/` for root) |
| `--commit-specifier` | No | string | HEAD | Branch, tag, or commit ID |

**Output Schema:**
```json
{
    "commitId": "string",
    "folderPath": "string",
    "treeId": "string",
    "subFolders": [
        {
            "treeId": "string",
            "absolutePath": "string",
            "relativePath": "string"
        }
    ],
    "files": [
        {
            "blobId": "string",
            "absolutePath": "string",
            "relativePath": "string",
            "fileMode": "EXECUTABLE|NORMAL|SYMLINK"
        }
    ],
    "symbolicLinks": [
        {
            "blobId": "string",
            "absolutePath": "string",
            "relativePath": "string",
            "fileMode": "SYMLINK"
        }
    ],
    "subModules": [
        {
            "commitId": "string",
            "absolutePath": "string",
            "relativePath": "string"
        }
    ]
}
```

---

### 3.8 `put-file`

Adds or updates a single file in a branch.

**Synopsis:**
```bash
aws codecommit put-file \
    --repository-name <value> \
    --branch-name <value> \
    --file-content <value> \
    --file-path <value> \
    [--file-mode <value>] \
    [--parent-commit-id <value>] \
    [--commit-message <value>] \
    [--name <value>] \
    [--email <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--branch-name` | **Yes** | string | -- | Name of the branch |
| `--file-content` | **Yes** | blob | -- | Content of the file (base64-encoded) |
| `--file-path` | **Yes** | string | -- | Full path to the file |
| `--file-mode` | No | string | `NORMAL` | File mode: `EXECUTABLE`, `NORMAL`, `SYMLINK` |
| `--parent-commit-id` | No | string | -- | Full commit ID of the head of the branch |
| `--commit-message` | No | string | -- | Commit message |
| `--name` | No | string | -- | Name of the committer |
| `--email` | No | string | -- | Email of the committer |

**Output Schema:**
```json
{
    "commitId": "string",
    "blobId": "string",
    "treeId": "string"
}
```

---

### 3.9 `delete-file`

Deletes a specified file from a specified branch.

**Synopsis:**
```bash
aws codecommit delete-file \
    --repository-name <value> \
    --branch-name <value> \
    --file-path <value> \
    --parent-commit-id <value> \
    [--keep-empty-folders | --no-keep-empty-folders] \
    [--commit-message <value>] \
    [--name <value>] \
    [--email <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--branch-name` | **Yes** | string | -- | Name of the branch |
| `--file-path` | **Yes** | string | -- | Full path of the file to delete |
| `--parent-commit-id` | **Yes** | string | -- | Full commit ID of the head of the branch |
| `--keep-empty-folders` | No | boolean | false | Keep empty folders after deletion |
| `--commit-message` | No | string | -- | Commit message |
| `--name` | No | string | -- | Name of the committer |
| `--email` | No | string | -- | Email of the committer |

**Output Schema:**
```json
{
    "commitId": "string",
    "blobId": "string",
    "treeId": "string",
    "filePath": "string"
}
```
