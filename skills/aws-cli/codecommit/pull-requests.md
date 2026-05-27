# Pull Requests

### 4.1 `create-pull-request`

Creates a pull request in the specified repository.

**Synopsis:**
```bash
aws codecommit create-pull-request \
    --title <value> \
    --targets <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--title` | **Yes** | string | -- | Title of the pull request |
| `--targets` | **Yes** | list | -- | Targets for the PR. Shorthand: `repositoryName=string,sourceReference=string,destinationReference=string ...` |
| `--description` | No | string | -- | Description of the pull request |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "description": "string",
        "lastActivityDate": "timestamp",
        "creationDate": "timestamp",
        "pullRequestStatus": "OPEN|CLOSED",
        "authorArn": "string",
        "pullRequestTargets": [
            {
                "repositoryName": "string",
                "sourceReference": "string",
                "destinationReference": "string",
                "destinationCommit": "string",
                "sourceCommit": "string",
                "mergeBase": "string",
                "mergeMetadata": {
                    "isMerged": "boolean",
                    "mergedBy": "string",
                    "mergeCommitId": "string",
                    "mergeOption": "FAST_FORWARD_MERGE|SQUASH_MERGE|THREE_WAY_MERGE"
                }
            }
        ],
        "clientRequestToken": "string",
        "revisionId": "string",
        "approvalRules": [
            {
                "approvalRuleId": "string",
                "approvalRuleName": "string",
                "approvalRuleContent": "string",
                "ruleContentSha256": "string",
                "lastModifiedDate": "timestamp",
                "creationDate": "timestamp",
                "lastModifiedUser": "string",
                "originApprovalRuleTemplate": {
                    "approvalRuleTemplateId": "string",
                    "approvalRuleTemplateName": "string"
                }
            }
        ]
    }
}
```

---

### 4.2 `get-pull-request`

Gets information about a pull request.

**Synopsis:**
```bash
aws codecommit get-pull-request \
    --pull-request-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "description": "string",
        "lastActivityDate": "timestamp",
        "creationDate": "timestamp",
        "pullRequestStatus": "OPEN|CLOSED",
        "authorArn": "string",
        "pullRequestTargets": [
            {
                "repositoryName": "string",
                "sourceReference": "string",
                "destinationReference": "string",
                "destinationCommit": "string",
                "sourceCommit": "string",
                "mergeBase": "string",
                "mergeMetadata": {}
            }
        ],
        "clientRequestToken": "string",
        "revisionId": "string",
        "approvalRules": []
    }
}
```

---

### 4.3 `list-pull-requests`

Returns a list of pull requests for a repository. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit list-pull-requests \
    --repository-name <value> \
    [--author-arn <value>] \
    [--pull-request-status <value>] \
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
| `--author-arn` | No | string | -- | Filter by author ARN |
| `--pull-request-status` | No | string | `OPEN` | Filter by status: `OPEN`, `CLOSED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "pullRequestIds": ["string"],
    "nextToken": "string"
}
```

---

### 4.4 `update-pull-request-title`

Updates the title of a pull request.

**Synopsis:**
```bash
aws codecommit update-pull-request-title \
    --pull-request-id <value> \
    --title <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--title` | **Yes** | string | -- | New title for the pull request |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "description": "string",
        "pullRequestStatus": "OPEN|CLOSED",
        "authorArn": "string",
        "pullRequestTargets": [],
        "revisionId": "string"
    }
}
```

---

### 4.5 `update-pull-request-description`

Updates the description of a pull request.

**Synopsis:**
```bash
aws codecommit update-pull-request-description \
    --pull-request-id <value> \
    --description <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--description` | **Yes** | string | -- | New description for the pull request |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "description": "string",
        "pullRequestStatus": "OPEN|CLOSED",
        "authorArn": "string",
        "pullRequestTargets": [],
        "revisionId": "string"
    }
}
```

---

### 4.6 `update-pull-request-status`

Updates the status of a pull request (open or close).

**Synopsis:**
```bash
aws codecommit update-pull-request-status \
    --pull-request-id <value> \
    --pull-request-status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--pull-request-status` | **Yes** | string | -- | Status: `OPEN`, `CLOSED` |

**Output Schema:**
```json
{
    "pullRequest": {
        "pullRequestId": "string",
        "title": "string",
        "description": "string",
        "pullRequestStatus": "OPEN|CLOSED",
        "authorArn": "string",
        "pullRequestTargets": [],
        "revisionId": "string"
    }
}
```

---

### 4.7 `describe-pull-request-events`

Returns information about events in pull requests. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit describe-pull-request-events \
    --pull-request-id <value> \
    [--pull-request-event-type <value>] \
    [--actor-arn <value>] \
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
| `--pull-request-event-type` | No | string | -- | Event type filter: `PULL_REQUEST_CREATED`, `PULL_REQUEST_STATUS_CHANGED`, `PULL_REQUEST_SOURCE_REFERENCE_UPDATED`, `PULL_REQUEST_MERGE_STATE_CHANGED`, `PULL_REQUEST_APPROVAL_RULE_CREATED`, `PULL_REQUEST_APPROVAL_RULE_UPDATED`, `PULL_REQUEST_APPROVAL_RULE_DELETED`, `PULL_REQUEST_APPROVAL_RULE_OVERRIDDEN`, `PULL_REQUEST_APPROVAL_STATE_CHANGED` |
| `--actor-arn` | No | string | -- | Filter by actor ARN |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "pullRequestEvents": [
        {
            "pullRequestId": "string",
            "eventDate": "timestamp",
            "pullRequestEventType": "string",
            "actorArn": "string",
            "pullRequestCreatedEventMetadata": {
                "repositoryName": "string",
                "sourceCommitId": "string",
                "destinationCommitId": "string",
                "mergeBase": "string"
            },
            "pullRequestStatusChangedEventMetadata": {
                "pullRequestStatus": "OPEN|CLOSED"
            },
            "pullRequestSourceReferenceUpdatedEventMetadata": {
                "repositoryName": "string",
                "beforeCommitId": "string",
                "afterCommitId": "string",
                "mergeBase": "string"
            },
            "pullRequestMergedStateChangedEventMetadata": {
                "repositoryName": "string",
                "destinationReference": "string",
                "mergeMetadata": {}
            },
            "approvalRuleEventMetadata": {
                "approvalRuleName": "string",
                "approvalRuleId": "string",
                "approvalRuleContent": "string"
            },
            "approvalStateChangedEventMetadata": {
                "revisionId": "string",
                "approvalStatus": "APPROVE|REVOKE"
            },
            "approvalRuleOverriddenEventMetadata": {
                "revisionId": "string",
                "overrideStatus": "OVERRIDE|REVOKE"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.8 `evaluate-pull-request-approval-rules`

Evaluates whether a pull request has met all the conditions specified in its approval rules.

**Synopsis:**
```bash
aws codecommit evaluate-pull-request-approval-rules \
    --pull-request-id <value> \
    --revision-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pull-request-id` | **Yes** | string | -- | System-generated ID of the pull request |
| `--revision-id` | **Yes** | string | -- | Revision ID of the pull request |

**Output Schema:**
```json
{
    "evaluation": {
        "approved": "boolean",
        "overridden": "boolean",
        "approvalRulesSatisfied": ["string"],
        "approvalRulesNotSatisfied": ["string"]
    }
}
```
