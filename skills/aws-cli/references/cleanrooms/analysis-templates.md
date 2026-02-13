# Analysis Templates

## 4.1 `create-analysis-template`

Creates an analysis template within a membership.

**Synopsis:**
```bash
aws cleanrooms create-analysis-template \
    --membership-identifier <value> \
    --name <value> \
    --format <value> \
    --source <value> \
    [--description <value>] \
    [--analysis-parameters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID or ARN |
| `--name` | **Yes** | string | -- | Template name |
| `--format` | **Yes** | string | -- | Format: `SQL` |
| `--source` | **Yes** | structure | -- | Template source. Shorthand: `text=string` |
| `--description` | No | string | None | Description |
| `--analysis-parameters` | No | list | None | Parameters for the template |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "analysisTemplate": {
        "id": "string",
        "arn": "string",
        "collaborationId": "string",
        "collaborationArn": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "description": "string",
        "name": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "schema": {
            "referencedTables": ["string"]
        },
        "format": "SQL",
        "source": {
            "text": "string"
        },
        "analysisParameters": [
            {
                "name": "string",
                "type": "SMALLINT|INTEGER|BIGINT|DECIMAL|REAL|DOUBLE_PRECISION|BOOLEAN|CHAR|VARCHAR|DATE|TIMESTAMP|TIMESTAMPTZ|TIME|TIMETZ|VARBYTE",
                "defaultValue": "string"
            }
        ]
    }
}
```

---

## 4.2 `delete-analysis-template`

Deletes an analysis template.

**Synopsis:**
```bash
aws cleanrooms delete-analysis-template \
    --membership-identifier <value> \
    --analysis-template-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--analysis-template-identifier` | **Yes** | string | -- | Analysis template ID |

**Output Schema:**

None (HTTP 204 on success).

---

## 4.3 `get-analysis-template`

Returns details for an analysis template.

**Synopsis:**
```bash
aws cleanrooms get-analysis-template \
    --membership-identifier <value> \
    --analysis-template-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--analysis-template-identifier` | **Yes** | string | -- | Analysis template ID |

**Output Schema:**
```json
{
    "analysisTemplate": {
        "id": "string",
        "arn": "string",
        "collaborationId": "string",
        "membershipId": "string",
        "name": "string",
        "description": "string",
        "format": "SQL",
        "source": { "text": "string" },
        "schema": { "referencedTables": ["string"] },
        "analysisParameters": [],
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 4.4 `list-analysis-templates`

Lists analysis templates for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-analysis-templates \
    --membership-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "analysisTemplateSummaries": [
        {
            "arn": "string",
            "createTime": "timestamp",
            "id": "string",
            "name": "string",
            "updateTime": "timestamp",
            "membershipArn": "string",
            "membershipId": "string",
            "collaborationArn": "string",
            "collaborationId": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 4.5 `update-analysis-template`

Updates an analysis template description.

**Synopsis:**
```bash
aws cleanrooms update-analysis-template \
    --membership-identifier <value> \
    --analysis-template-identifier <value> \
    [--description <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--analysis-template-identifier` | **Yes** | string | -- | Analysis template ID |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "analysisTemplate": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "updateTime": "timestamp"
    }
}
```

---

## 4.6 `batch-get-collaboration-analysis-template`

Retrieves multiple collaboration analysis templates.

**Synopsis:**
```bash
aws cleanrooms batch-get-collaboration-analysis-template \
    --collaboration-identifier <value> \
    --analysis-template-arns <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--analysis-template-arns` | **Yes** | list(string) | -- | List of analysis template ARNs |

**Output Schema:**
```json
{
    "collaborationAnalysisTemplates": [
        {
            "id": "string",
            "arn": "string",
            "collaborationId": "string",
            "collaborationArn": "string",
            "creatorAccountId": "string",
            "name": "string",
            "description": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "schema": {},
            "format": "SQL",
            "source": {},
            "analysisParameters": []
        }
    ],
    "errors": [
        {
            "arn": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

## 4.7 `get-collaboration-analysis-template`

Gets a collaboration analysis template.

**Synopsis:**
```bash
aws cleanrooms get-collaboration-analysis-template \
    --collaboration-identifier <value> \
    --analysis-template-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--analysis-template-arn` | **Yes** | string | -- | Analysis template ARN |

**Output Schema:**
```json
{
    "collaborationAnalysisTemplate": {
        "id": "string",
        "arn": "string",
        "collaborationId": "string",
        "creatorAccountId": "string",
        "name": "string",
        "description": "string",
        "format": "SQL",
        "source": { "text": "string" },
        "schema": { "referencedTables": ["string"] },
        "analysisParameters": [],
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 4.8 `list-collaboration-analysis-templates`

Lists collaboration analysis templates. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-collaboration-analysis-templates \
    --collaboration-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "collaborationAnalysisTemplateSummaries": [
        {
            "arn": "string",
            "createTime": "timestamp",
            "id": "string",
            "name": "string",
            "updateTime": "timestamp",
            "collaborationArn": "string",
            "collaborationId": "string",
            "creatorAccountId": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```
