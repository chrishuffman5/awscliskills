# Schemas

## 5.1 `batch-get-schema`

Retrieves multiple schemas for a collaboration.

**Synopsis:**
```bash
aws cleanrooms batch-get-schema \
    --collaboration-identifier <value> \
    --names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--names` | **Yes** | list(string) | -- | Schema names to retrieve |

**Output Schema:**
```json
{
    "schemas": [
        {
            "columns": [
                {
                    "name": "string",
                    "type": "string"
                }
            ],
            "partitionKeys": [
                {
                    "name": "string",
                    "type": "string"
                }
            ],
            "analysisRuleTypes": ["AGGREGATION|LIST|CUSTOM"],
            "analysisMethod": "DIRECT_QUERY",
            "creatorAccountId": "string",
            "name": "string",
            "collaborationId": "string",
            "collaborationArn": "string",
            "description": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "type": "TABLE",
            "schemaStatusDetails": [
                {
                    "status": "READY|NOT_READY",
                    "reasons": [
                        {
                            "code": "ANALYSIS_RULE_MISSING|ANALYSIS_TEMPLATES_NOT_CONFIGURED|ANALYSIS_PROVIDERS_NOT_CONFIGURED|DIFFERENTIAL_PRIVACY_POLICY_NOT_CONFIGURED",
                            "message": "string"
                        }
                    ],
                    "analysisRuleType": "string",
                    "configurations": ["string"]
                }
            ]
        }
    ],
    "errors": [
        {
            "name": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

## 5.2 `batch-get-schema-analysis-rule`

Retrieves multiple schema analysis rules.

**Synopsis:**
```bash
aws cleanrooms batch-get-schema-analysis-rule \
    --collaboration-identifier <value> \
    --schema-analysis-rule-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--schema-analysis-rule-requests` | **Yes** | list | -- | List of schema name + rule type pairs |

**Request Structure:**
```json
[
    {
        "name": "schema-name",
        "type": "AGGREGATION"
    }
]
```

**Output Schema:**
```json
{
    "analysisRules": [
        {
            "collaborationId": "string",
            "type": "AGGREGATION|LIST|CUSTOM",
            "name": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "policy": {}
        }
    ],
    "errors": [
        {
            "name": "string",
            "type": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

## 5.3 `get-schema`

Returns a schema for a collaboration.

**Synopsis:**
```bash
aws cleanrooms get-schema \
    --collaboration-identifier <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--name` | **Yes** | string | -- | Schema name |

**Output Schema:**
```json
{
    "schema": {
        "columns": [
            { "name": "string", "type": "string" }
        ],
        "partitionKeys": [],
        "analysisRuleTypes": ["string"],
        "analysisMethod": "DIRECT_QUERY",
        "creatorAccountId": "string",
        "name": "string",
        "collaborationId": "string",
        "collaborationArn": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "type": "TABLE",
        "schemaStatusDetails": []
    }
}
```

---

## 5.4 `get-schema-analysis-rule`

Returns a specific schema analysis rule.

**Synopsis:**
```bash
aws cleanrooms get-schema-analysis-rule \
    --collaboration-identifier <value> \
    --name <value> \
    --type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--name` | **Yes** | string | -- | Schema name |
| `--type` | **Yes** | string | -- | Rule type: `AGGREGATION`, `LIST`, or `CUSTOM` |

**Output Schema:**
```json
{
    "analysisRule": {
        "collaborationId": "string",
        "type": "AGGREGATION|LIST|CUSTOM",
        "name": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "policy": {
            "v1": {
                "aggregation": {},
                "list": {},
                "custom": {}
            }
        }
    }
}
```

---

## 5.5 `list-schemas`

Lists schemas for a collaboration. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-schemas \
    --collaboration-identifier <value> \
    [--schema-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--schema-type` | No | string | None | Filter by type: `TABLE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "schemaSummaries": [
        {
            "name": "string",
            "type": "TABLE",
            "creatorAccountId": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "collaborationId": "string",
            "collaborationArn": "string",
            "analysisRuleTypes": ["string"],
            "analysisMethod": "string"
        }
    ],
    "nextToken": "string"
}
```
