# Profiles

### 6.1 `create-profile`

Creates a Well-Architected profile.

**Synopsis:**
```bash
aws wellarchitected create-profile \
    --profile-name <value> \
    --profile-description <value> \
    --profile-questions <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-name` | **Yes** | string | -- | Profile name (3-100 chars) |
| `--profile-description` | **Yes** | string | -- | Description (3-100 chars) |
| `--profile-questions` | **Yes** | list | -- | Question updates. JSON: `[{QuestionId,SelectedChoiceIds}]` |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Tags (1-50 tags) |

**Output Schema:**
```json
{
    "ProfileArn": "string",
    "ProfileVersion": "string"
}
```

---

### 6.2 `delete-profile`

Deletes a profile.

**Synopsis:**
```bash
aws wellarchitected delete-profile \
    --profile-arn <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-arn` | **Yes** | string | -- | Profile ARN |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
None
```

---

### 6.3 `get-profile`

Retrieves a profile.

**Synopsis:**
```bash
aws wellarchitected get-profile \
    --profile-arn <value> \
    [--profile-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-arn` | **Yes** | string | -- | Profile ARN |
| `--profile-version` | No | string | None | Specific version |

**Output Schema:**
```json
{
    "Profile": {
        "ProfileArn": "string",
        "ProfileVersion": "string",
        "ProfileName": "string",
        "ProfileDescription": "string",
        "ProfileQuestions": [
            {
                "QuestionId": "string",
                "QuestionTitle": "string",
                "QuestionDescription": "string",
                "QuestionChoices": [
                    {"ChoiceId": "string", "ChoiceTitle": "string", "ChoiceDescription": "string"}
                ],
                "SelectedChoiceIds": ["string"],
                "MinSelectedChoices": "integer",
                "MaxSelectedChoices": "integer"
            }
        ],
        "Owner": "string",
        "CreatedAt": "timestamp",
        "UpdatedAt": "timestamp",
        "ShareInvitationId": "string",
        "Tags": {"string": "string"}
    }
}
```

---

### 6.4 `list-profiles`

Lists all profiles. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-profiles \
    [--profile-name-prefix <value>] \
    [--profile-owner-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-name-prefix` | No | string | None | Filter by name prefix |
| `--profile-owner-type` | No | string | None | `SELF` or `SHARED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProfileSummaries": [
        {
            "ProfileArn": "string",
            "ProfileVersion": "string",
            "ProfileName": "string",
            "ProfileDescription": "string",
            "Owner": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-profile`

Updates a profile.

**Synopsis:**
```bash
aws wellarchitected update-profile \
    --profile-arn <value> \
    [--profile-description <value>] \
    [--profile-questions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-arn` | **Yes** | string | -- | Profile ARN |
| `--profile-description` | No | string | None | New description |
| `--profile-questions` | No | list | None | Updated questions |

**Output Schema:**
```json
{
    "Profile": {
        "ProfileArn": "string",
        "ProfileVersion": "string",
        "ProfileName": "string"
    }
}
```

---

### 6.6 `get-profile-template`

Retrieves the profile template with available questions and choices.

**Synopsis:**
```bash
aws wellarchitected get-profile-template \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| (none) | -- | -- | -- | No parameters required |

**Output Schema:**
```json
{
    "ProfileTemplate": {
        "TemplateName": "string",
        "TemplateQuestions": [
            {
                "QuestionId": "string",
                "QuestionTitle": "string",
                "QuestionDescription": "string",
                "QuestionChoices": [
                    {"ChoiceId": "string", "ChoiceTitle": "string", "ChoiceDescription": "string"}
                ],
                "MinSelectedChoices": "integer",
                "MaxSelectedChoices": "integer"
            }
        ],
        "CreatedAt": "timestamp",
        "UpdatedAt": "timestamp"
    }
}
```

---

### 6.7 `create-profile-share`

Shares a profile with another account.

**Synopsis:**
```bash
aws wellarchitected create-profile-share \
    --profile-arn <value> \
    --shared-with <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-arn` | **Yes** | string | -- | Profile ARN |
| `--shared-with` | **Yes** | string | -- | Account ID, org ID, or OU ID |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "ShareId": "string",
    "ProfileArn": "string"
}
```

---

### 6.8 `delete-profile-share`

Deletes a profile share.

**Synopsis:**
```bash
aws wellarchitected delete-profile-share \
    --share-id <value> \
    --profile-arn <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--share-id` | **Yes** | string | -- | Share ID |
| `--profile-arn` | **Yes** | string | -- | Profile ARN |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
None
```

---

### 6.9 `list-profile-shares`

Lists shares for a profile. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-profile-shares \
    --profile-arn <value> \
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
| `--profile-arn` | **Yes** | string | -- | Profile ARN |
| `--shared-with-prefix` | No | string | None | Filter by shared-with prefix |
| `--status` | No | string | None | Filter by share status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProfileShareSummaries": [
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

---

### 6.10 `list-profile-notifications`

Lists profile notifications. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-profile-notifications \
    [--workload-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | No | string | None | Filter by workload |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NotificationSummaries": [
        {
            "CurrentProfileVersion": "string",
            "LatestProfileVersion": "string",
            "Type": "PROFILE_ANSWERS_UPDATED|PROFILE_DELETED",
            "ProfileArn": "string",
            "ProfileName": "string",
            "WorkloadId": "string",
            "WorkloadName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.11 `upgrade-profile-version`

Upgrades a profile to the latest version.

**Synopsis:**
```bash
aws wellarchitected upgrade-profile-version \
    --workload-id <value> \
    --profile-arn <value> \
    [--milestone-name <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--profile-arn` | **Yes** | string | -- | Profile ARN |
| `--milestone-name` | No | string | None | Milestone name for upgrade snapshot |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
None
```

---

### 6.12 `associate-profiles`

Associates profiles with a workload.

**Synopsis:**
```bash
aws wellarchitected associate-profiles \
    --workload-id <value> \
    --profile-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--profile-arns` | **Yes** | list(string) | -- | Profile ARNs to associate |

**Output Schema:**
```json
None
```

---

### 6.13 `disassociate-profiles`

Disassociates profiles from a workload.

**Synopsis:**
```bash
aws wellarchitected disassociate-profiles \
    --workload-id <value> \
    --profile-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--profile-arns` | **Yes** | list(string) | -- | Profile ARNs to disassociate |

**Output Schema:**
```json
None
```
