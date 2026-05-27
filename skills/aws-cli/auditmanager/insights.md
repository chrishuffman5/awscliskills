# Insights

### 7.1 `get-insights`

Returns cross-assessment compliance insights for all active assessments.

**Synopsis:**
```bash
aws auditmanager get-insights \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "insights": {
        "activeAssessmentsCount": "integer",
        "noncompliantEvidenceCount": "integer",
        "compliantEvidenceCount": "integer",
        "inconclusiveEvidenceCount": "integer",
        "assessmentControlsCountByNoncompliantEvidence": "integer",
        "totalAssessmentControlsCount": "integer",
        "lastUpdated": "timestamp"
    }
}
```

---

### 7.2 `get-insights-by-assessment`

Returns compliance insights for a specific assessment.

**Synopsis:**
```bash
aws auditmanager get-insights-by-assessment \
    --assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |

**Output Schema:**
```json
{
    "insights": {
        "noncompliantEvidenceCount": "integer",
        "compliantEvidenceCount": "integer",
        "inconclusiveEvidenceCount": "integer",
        "assessmentControlsCountByNoncompliantEvidence": "integer",
        "totalAssessmentControlsCount": "integer",
        "lastUpdated": "timestamp"
    }
}
```

---

### 7.3 `list-assessment-control-insights-by-control-domain`

Lists control insights for assessments grouped by control domain. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-assessment-control-insights-by-control-domain \
    --control-domain-id <value> \
    --assessment-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-domain-id` | **Yes** | string | -- | Control domain ID (UUID) |
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "controlInsightsByAssessment": [
        {
            "name": "string",
            "id": "string",
            "evidenceInsights": {
                "noncompliantEvidenceCount": "integer",
                "compliantEvidenceCount": "integer",
                "inconclusiveEvidenceCount": "integer"
            },
            "controlSetName": "string",
            "lastUpdated": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `list-control-domain-insights`

Lists control domain insights across all active assessments. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-control-domain-insights \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "controlDomainInsights": [
        {
            "name": "string",
            "id": "string",
            "controlsCountByNoncompliantEvidence": "integer",
            "totalControlsCount": "integer",
            "evidenceInsights": {
                "noncompliantEvidenceCount": "integer",
                "compliantEvidenceCount": "integer",
                "inconclusiveEvidenceCount": "integer"
            },
            "lastUpdated": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.5 `list-control-domain-insights-by-assessment`

Lists control domain insights for a specific assessment. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-control-domain-insights-by-assessment \
    --assessment-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:** Same as `list-control-domain-insights`.

---

### 7.6 `list-control-insights-by-control-domain`

Lists control-level insights by control domain across all active assessments. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-control-insights-by-control-domain \
    --control-domain-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-domain-id` | **Yes** | string | -- | Control domain ID (UUID) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "controlInsightsMetadata": [
        {
            "name": "string",
            "id": "string",
            "evidenceInsights": {
                "noncompliantEvidenceCount": "integer",
                "compliantEvidenceCount": "integer",
                "inconclusiveEvidenceCount": "integer"
            },
            "lastUpdated": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
