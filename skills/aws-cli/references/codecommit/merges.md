# Merges

### 6.1 `get-merge-options`

Returns information about the available merge options between two branches or commit specifiers.

**Synopsis:**
```bash
aws codecommit get-merge-options \
    --repository-name <value> \
    --source-commit-specifier <value> \
    --destination-commit-specifier <value> \
    [--conflict-detail-level <value>] \
    [--conflict-resolution-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-specifier` | **Yes** | string | -- | Branch, tag, HEAD, or commit ID for source |
| `--destination-commit-specifier` | **Yes** | string | -- | Branch, tag, HEAD, or commit ID for destination |
| `--conflict-detail-level` | No | string | `FILE_LEVEL` | Detail level: `FILE_LEVEL`, `LINE_LEVEL` |
| `--conflict-resolution-strategy` | No | string | `NONE` | Strategy: `NONE`, `ACCEPT_SOURCE`, `ACCEPT_DESTINATION`, `AUTOMERGE` |

**Output Schema:**
```json
{
    "mergeOptions": ["FAST_FORWARD_MERGE", "SQUASH_MERGE", "THREE_WAY_MERGE"],
    "sourceCommitId": "string",
    "destinationCommitId": "string",
    "baseCommitId": "string"
}
```

---

### 6.2 `get-merge-conflicts`

Returns information about merge conflicts between source and destination in a pull request. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit get-merge-conflicts \
    --repository-name <value> \
    --destination-commit-specifier <value> \
    --source-commit-specifier <value> \
    --merge-option <value> \
    [--conflict-detail-level <value>] \
    [--conflict-resolution-strategy <value>] \
    [--max-conflict-files <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--destination-commit-specifier` | **Yes** | string | -- | Destination commit specifier |
| `--source-commit-specifier` | **Yes** | string | -- | Source commit specifier |
| `--merge-option` | **Yes** | string | -- | Merge option: `FAST_FORWARD_MERGE`, `SQUASH_MERGE`, `THREE_WAY_MERGE` |
| `--conflict-detail-level` | No | string | `FILE_LEVEL` | Detail level: `FILE_LEVEL`, `LINE_LEVEL` |
| `--conflict-resolution-strategy` | No | string | `NONE` | Resolution strategy |
| `--max-conflict-files` | No | integer | -- | Maximum number of conflict files |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "mergeable": "boolean",
    "destinationCommitId": "string",
    "sourceCommitId": "string",
    "baseCommitId": "string",
    "conflictMetadataList": [
        {
            "filePath": "string",
            "fileSizes": {
                "source": "long",
                "destination": "long",
                "base": "long"
            },
            "fileModes": {
                "source": "EXECUTABLE|NORMAL|SYMLINK",
                "destination": "EXECUTABLE|NORMAL|SYMLINK",
                "base": "EXECUTABLE|NORMAL|SYMLINK"
            },
            "objectTypes": {
                "source": "FILE|DIRECTORY|GIT_LINK|SYMBOLIC_LINK",
                "destination": "FILE|DIRECTORY|GIT_LINK|SYMBOLIC_LINK",
                "base": "FILE|DIRECTORY|GIT_LINK|SYMBOLIC_LINK"
            },
            "numberOfConflicts": "integer",
            "isBinaryFile": {
                "source": "boolean",
                "destination": "boolean",
                "base": "boolean"
            },
            "contentConflict": "boolean",
            "fileModeConflict": "boolean",
            "objectTypeConflict": "boolean",
            "mergeOperations": {
                "source": "A|M|D",
                "destination": "A|M|D"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 6.3 `get-merge-commit`

Returns information about a specified merge commit.

**Synopsis:**
```bash
aws codecommit get-merge-commit \
    --repository-name <value> \
    --source-commit-specifier <value> \
    --destination-commit-specifier <value> \
    [--conflict-detail-level <value>] \
    [--conflict-resolution-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-specifier` | **Yes** | string | -- | Source commit specifier |
| `--destination-commit-specifier` | **Yes** | string | -- | Destination commit specifier |
| `--conflict-detail-level` | No | string | `FILE_LEVEL` | Detail level |
| `--conflict-resolution-strategy` | No | string | `NONE` | Resolution strategy |

**Output Schema:**
```json
{
    "sourceCommitId": "string",
    "destinationCommitId": "string",
    "baseCommitId": "string",
    "mergedCommitId": "string"
}
```

---

### 6.4 `merge-branches-by-fast-forward`

Merges two branches using the fast-forward merge strategy.

**Synopsis:**
```bash
aws codecommit merge-branches-by-fast-forward \
    --repository-name <value> \
    --source-commit-specifier <value> \
    --destination-commit-specifier <value> \
    [--target-branch <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-specifier` | **Yes** | string | -- | Source branch or commit |
| `--destination-commit-specifier` | **Yes** | string | -- | Destination branch or commit |
| `--target-branch` | No | string | -- | Branch to update with the merge result |

**Output Schema:**
```json
{
    "commitId": "string",
    "treeId": "string"
}
```

---

### 6.5 `merge-branches-by-squash`

Merges two branches using the squash merge strategy.

**Synopsis:**
```bash
aws codecommit merge-branches-by-squash \
    --repository-name <value> \
    --source-commit-specifier <value> \
    --destination-commit-specifier <value> \
    [--target-branch <value>] \
    [--conflict-detail-level <value>] \
    [--conflict-resolution-strategy <value>] \
    [--conflict-resolution <value>] \
    [--author-name <value>] \
    [--email <value>] \
    [--commit-message <value>] \
    [--keep-empty-folders | --no-keep-empty-folders] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-specifier` | **Yes** | string | -- | Source branch or commit |
| `--destination-commit-specifier` | **Yes** | string | -- | Destination branch or commit |
| `--target-branch` | No | string | -- | Branch to update with the merge result |
| `--conflict-detail-level` | No | string | `FILE_LEVEL` | Detail level |
| `--conflict-resolution-strategy` | No | string | `NONE` | Resolution strategy |
| `--conflict-resolution` | No | structure | -- | Conflict resolution structure |
| `--author-name` | No | string | -- | Author name |
| `--email` | No | string | -- | Author email |
| `--commit-message` | No | string | -- | Commit message |
| `--keep-empty-folders` | No | boolean | false | Keep empty folders |

**Output Schema:**
```json
{
    "commitId": "string",
    "treeId": "string"
}
```

---

### 6.6 `merge-branches-by-three-way`

Merges two branches using the three-way merge strategy.

**Synopsis:**
```bash
aws codecommit merge-branches-by-three-way \
    --repository-name <value> \
    --source-commit-specifier <value> \
    --destination-commit-specifier <value> \
    [--target-branch <value>] \
    [--conflict-detail-level <value>] \
    [--conflict-resolution-strategy <value>] \
    [--conflict-resolution <value>] \
    [--author-name <value>] \
    [--email <value>] \
    [--commit-message <value>] \
    [--keep-empty-folders | --no-keep-empty-folders] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-specifier` | **Yes** | string | -- | Source branch or commit |
| `--destination-commit-specifier` | **Yes** | string | -- | Destination branch or commit |
| `--target-branch` | No | string | -- | Branch to update |
| `--conflict-detail-level` | No | string | `FILE_LEVEL` | Detail level |
| `--conflict-resolution-strategy` | No | string | `NONE` | Resolution strategy |
| `--conflict-resolution` | No | structure | -- | Conflict resolution structure |
| `--author-name` | No | string | -- | Author name |
| `--email` | No | string | -- | Author email |
| `--commit-message` | No | string | -- | Commit message |
| `--keep-empty-folders` | No | boolean | false | Keep empty folders |

**Output Schema:**
```json
{
    "commitId": "string",
    "treeId": "string"
}
```

---

### 6.7 `merge-pull-request-by-fast-forward`

Attempts to merge the source commit of a pull request into the destination branch using fast-forward.

**Synopsis:**
```bash
aws codecommit merge-pull-request-by-fast-forward \
    --pull-request-id <value> \
    --repository-name <value> \
    [--source-commit-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-id` | No | string | -- | Full commit ID of the source tip (for validation) |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "pullRequestStatus": "OPEN|CLOSED",
        "pullRequestTargets": [
            {
                "repositoryName": "string",
                "sourceReference": "string",
                "destinationReference": "string",
                "mergeMetadata": {
                    "isMerged": "boolean",
                    "mergedBy": "string",
                    "mergeCommitId": "string",
                    "mergeOption": "FAST_FORWARD_MERGE"
                }
            }
        ]
    }
}
```

---

### 6.8 `merge-pull-request-by-squash`

Attempts to merge the source commit of a pull request into the destination branch using squash merge.

**Synopsis:**
```bash
aws codecommit merge-pull-request-by-squash \
    --pull-request-id <value> \
    --repository-name <value> \
    [--source-commit-id <value>] \
    [--conflict-detail-level <value>] \
    [--conflict-resolution-strategy <value>] \
    [--conflict-resolution <value>] \
    [--author-name <value>] \
    [--email <value>] \
    [--commit-message <value>] \
    [--keep-empty-folders | --no-keep-empty-folders] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-id` | No | string | -- | Full commit ID of the source tip |
| `--conflict-detail-level` | No | string | `FILE_LEVEL` | Detail level |
| `--conflict-resolution-strategy` | No | string | `NONE` | Resolution strategy |
| `--conflict-resolution` | No | structure | -- | Conflict resolution |
| `--author-name` | No | string | -- | Author name |
| `--email` | No | string | -- | Author email |
| `--commit-message` | No | string | -- | Commit message |
| `--keep-empty-folders` | No | boolean | false | Keep empty folders |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "pullRequestStatus": "OPEN|CLOSED",
        "pullRequestTargets": [
            {
                "mergeMetadata": {
                    "isMerged": "boolean",
                    "mergedBy": "string",
                    "mergeCommitId": "string",
                    "mergeOption": "SQUASH_MERGE"
                }
            }
        ]
    }
}
```

---

### 6.9 `merge-pull-request-by-three-way`

Attempts to merge the source commit of a pull request into the destination branch using three-way merge.

**Synopsis:**
```bash
aws codecommit merge-pull-request-by-three-way \
    --pull-request-id <value> \
    --repository-name <value> \
    [--source-commit-id <value>] \
    [--conflict-detail-level <value>] \
    [--conflict-resolution-strategy <value>] \
    [--conflict-resolution <value>] \
    [--author-name <value>] \
    [--email <value>] \
    [--commit-message <value>] \
    [--keep-empty-folders | --no-keep-empty-folders] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--source-commit-id` | No | string | -- | Full commit ID of the source tip |
| `--conflict-detail-level` | No | string | `FILE_LEVEL` | Detail level |
| `--conflict-resolution-strategy` | No | string | `NONE` | Resolution strategy |
| `--conflict-resolution` | No | structure | -- | Conflict resolution |
| `--author-name` | No | string | -- | Author name |
| `--email` | No | string | -- | Author email |
| `--commit-message` | No | string | -- | Commit message |
| `--keep-empty-folders` | No | boolean | false | Keep empty folders |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "pullRequestStatus": "OPEN|CLOSED",
        "pullRequestTargets": [
            {
                "mergeMetadata": {
                    "isMerged": "boolean",
                    "mergedBy": "string",
                    "mergeCommitId": "string",
                    "mergeOption": "THREE_WAY_MERGE"
                }
            }
        ]
    }
}
```
