# Comments

### 7.1 `post-comment-for-compared-commit`

Posts a comment on the comparison between two commits.

**Synopsis:**
```bash
aws codecommit post-comment-for-compared-commit \
    --repository-name <value> \
    --after-commit-id <value> \
    --content <value> \
    [--before-commit-id <value>] \
    [--location <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--after-commit-id` | **Yes** | string | -- | Commit ID for the after comparison |
| `--content` | **Yes** | string | -- | Content of the comment |
| `--before-commit-id` | No | string | -- | Commit ID for the before comparison |
| `--location` | No | structure | -- | Location in the comparison. Shorthand: `filePath=string,filePosition=long,relativeFileVersion=BEFORE\|AFTER` |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "repositoryName": "string",
    "beforeCommitId": "string",
    "afterCommitId": "string",
    "beforeBlobId": "string",
    "afterBlobId": "string",
    "location": {
        "filePath": "string",
        "filePosition": "long",
        "relativeFileVersion": "BEFORE|AFTER"
    },
    "comment": {
        "commentId": "string",
        "content": "string",
        "inReplyTo": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "authorArn": "string",
        "deleted": "boolean",
        "clientRequestToken": "string",
        "callerReactions": ["string"],
        "reactionCounts": {
            "string": "integer"
        }
    }
}
```

---

### 7.2 `post-comment-for-pull-request`

Posts a comment on a pull request.

**Synopsis:**
```bash
aws codecommit post-comment-for-pull-request \
    --pull-request-id <value> \
    --repository-name <value> \
    --before-commit-id <value> \
    --after-commit-id <value> \
    --content <value> \
    [--location <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--before-commit-id` | **Yes** | string | -- | Commit ID of the before comparison |
| `--after-commit-id` | **Yes** | string | -- | Commit ID of the after comparison |
| `--content` | **Yes** | string | -- | Content of the comment |
| `--location` | No | structure | -- | Location in the diff. Shorthand: `filePath=string,filePosition=long,relativeFileVersion=BEFORE\|AFTER` |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "repositoryName": "string",
    "pullRequestId": "string",
    "beforeCommitId": "string",
    "afterCommitId": "string",
    "beforeBlobId": "string",
    "afterBlobId": "string",
    "location": {
        "filePath": "string",
        "filePosition": "long",
        "relativeFileVersion": "BEFORE|AFTER"
    },
    "comment": {
        "commentId": "string",
        "content": "string",
        "inReplyTo": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "authorArn": "string",
        "deleted": "boolean",
        "clientRequestToken": "string"
    }
}
```

---

### 7.3 `post-comment-reply`

Posts a reply to a comment.

**Synopsis:**
```bash
aws codecommit post-comment-reply \
    --in-reply-to <value> \
    --content <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--in-reply-to` | **Yes** | string | -- | ID of the comment to reply to |
| `--content` | **Yes** | string | -- | Content of the reply |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "comment": {
        "commentId": "string",
        "content": "string",
        "inReplyTo": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "authorArn": "string",
        "deleted": "boolean",
        "clientRequestToken": "string"
    }
}
```

---

### 7.4 `get-comment`

Returns the content of a comment.

**Synopsis:**
```bash
aws codecommit get-comment \
    --comment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--comment-id` | **Yes** | string | -- | ID of the comment |

**Output Schema:**
```json
{
    "comment": {
        "commentId": "string",
        "content": "string",
        "inReplyTo": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "authorArn": "string",
        "deleted": "boolean",
        "clientRequestToken": "string",
        "callerReactions": ["string"],
        "reactionCounts": {
            "string": "integer"
        }
    }
}
```

---

### 7.5 `get-comments-for-compared-commit`

Returns comments for a comparison between two commits. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit get-comments-for-compared-commit \
    --repository-name <value> \
    --after-commit-id <value> \
    [--before-commit-id <value>] \
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
| `--after-commit-id` | **Yes** | string | -- | Commit ID for the after comparison |
| `--before-commit-id` | No | string | -- | Commit ID for the before comparison |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "commentsForComparedCommitData": [
        {
            "repositoryName": "string",
            "beforeCommitId": "string",
            "afterCommitId": "string",
            "beforeBlobId": "string",
            "afterBlobId": "string",
            "location": {
                "filePath": "string",
                "filePosition": "long",
                "relativeFileVersion": "BEFORE|AFTER"
            },
            "comments": [
                {
                    "commentId": "string",
                    "content": "string",
                    "inReplyTo": "string",
                    "creationDate": "timestamp",
                    "lastModifiedDate": "timestamp",
                    "authorArn": "string",
                    "deleted": "boolean"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 7.6 `get-comments-for-pull-request`

Returns comments for a pull request. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit get-comments-for-pull-request \
    --pull-request-id <value> \
    [--repository-name <value>] \
    [--before-commit-id <value>] \
    [--after-commit-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--repository-name` | No | string | -- | Name of the repository |
| `--before-commit-id` | No | string | -- | Before commit ID |
| `--after-commit-id` | No | string | -- | After commit ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "commentsForPullRequestData": [
        {
            "pullRequestId": "string",
            "repositoryName": "string",
            "beforeCommitId": "string",
            "afterCommitId": "string",
            "beforeBlobId": "string",
            "afterBlobId": "string",
            "location": {
                "filePath": "string",
                "filePosition": "long",
                "relativeFileVersion": "BEFORE|AFTER"
            },
            "comments": [
                {
                    "commentId": "string",
                    "content": "string",
                    "inReplyTo": "string",
                    "creationDate": "timestamp",
                    "lastModifiedDate": "timestamp",
                    "authorArn": "string",
                    "deleted": "boolean"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 7.7 `update-comment`

Replaces the content of a comment.

**Synopsis:**
```bash
aws codecommit update-comment \
    --comment-id <value> \
    --content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--comment-id` | **Yes** | string | -- | ID of the comment |
| `--content` | **Yes** | string | -- | New content for the comment |

**Output Schema:**
```json
{
    "comment": {
        "commentId": "string",
        "content": "string",
        "inReplyTo": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "authorArn": "string",
        "deleted": "boolean"
    }
}
```

---

### 7.8 `delete-comment-content`

Deletes the content of a comment. The comment itself is not deleted, but the content is replaced with a message indicating deletion.

**Synopsis:**
```bash
aws codecommit delete-comment-content \
    --comment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--comment-id` | **Yes** | string | -- | ID of the comment |

**Output Schema:**
```json
{
    "comment": {
        "commentId": "string",
        "content": "string",
        "inReplyTo": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "authorArn": "string",
        "deleted": "boolean"
    }
}
```
