# AD Assessments

### 11.1 `start-ad-assessment`

Starts an Active Directory assessment for a directory to identify configuration issues and recommendations.

**Synopsis:**
```bash
aws ds start-ad-assessment \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**
```json
{
    "AdAssessmentId": "string"
}
```

---

### 11.2 `delete-ad-assessment`

Deletes an AD assessment.

**Synopsis:**
```bash
aws ds delete-ad-assessment \
    --directory-id <value> \
    --ad-assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--ad-assessment-id` | **Yes** | string | -- | Assessment ID to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 11.3 `describe-ad-assessment`

Describes an AD assessment and its results.

**Synopsis:**
```bash
aws ds describe-ad-assessment \
    --directory-id <value> \
    --ad-assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--ad-assessment-id` | **Yes** | string | -- | Assessment ID |

**Output Schema:**
```json
{
    "AdAssessment": {
        "AdAssessmentId": "string",
        "DirectoryId": "string",
        "Status": "InProgress|Completed|Failed",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "Results": [
            {
                "Category": "string",
                "Severity": "Critical|Warning|Info",
                "Description": "string",
                "Recommendation": "string"
            }
        ]
    }
}
```

---

### 11.4 `list-ad-assessments`

Lists AD assessments for a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds list-ad-assessments \
    --directory-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AdAssessments": [
        {
            "AdAssessmentId": "string",
            "DirectoryId": "string",
            "Status": "InProgress|Completed|Failed",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
