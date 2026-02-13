# Encryption & Insights

### 8.1 `associate-encryption-config`

Associates an encryption configuration with an existing cluster to encrypt Kubernetes secrets.

**Synopsis:**
```bash
aws eks associate-encryption-config \
    --cluster-name <value> \
    --encryption-config <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--encryption-config` | **Yes** | list | -- | Encryption config. Shorthand: `resources=secrets,provider={keyArn=string}` |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "update": {
        "id": "string",
        "status": "InProgress|Failed|Cancelled|Successful",
        "type": "AssociateEncryptionConfig",
        "params": [
            {
                "type": "EncryptionConfig",
                "value": "string"
            }
        ],
        "createdAt": "timestamp",
        "errors": []
    }
}
```

---

### 8.2 `describe-insight`

Describes a cluster insight, which provides recommendations and findings about your EKS cluster.

**Synopsis:**
```bash
aws eks describe-insight \
    --cluster-name <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--id` | **Yes** | string | -- | Insight ID |

**Output Schema:**
```json
{
    "insight": {
        "id": "string",
        "name": "string",
        "category": "UPGRADE_READINESS",
        "kubernetesVersion": "string",
        "lastRefreshTime": "timestamp",
        "lastTransitionTime": "timestamp",
        "description": "string",
        "insightStatus": {
            "status": "PASSING|WARNING|ERROR|UNKNOWN",
            "reason": "string"
        },
        "recommendation": "string",
        "additionalInfo": {"string": "string"},
        "resources": [
            {
                "insightStatus": {
                    "status": "PASSING|WARNING|ERROR|UNKNOWN",
                    "reason": "string"
                },
                "kubernetesResourceUri": "string"
            }
        ],
        "categorySpecificSummary": {
            "deprecationDetails": [
                {
                    "usage": "string",
                    "replacedWith": "string",
                    "stopServingVersion": "string",
                    "startServingReplacementVersion": "string",
                    "clientStats": []
                }
            ]
        }
    }
}
```

---

### 8.3 `list-insights`

Lists insights for an EKS cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-insights \
    --cluster-name <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--filter` | No | structure | None | Filter. Shorthand: `categories=UPGRADE_READINESS,kubernetesVersions=string,statuses=PASSING\|WARNING\|ERROR\|UNKNOWN` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "insights": [
        {
            "id": "string",
            "name": "string",
            "category": "UPGRADE_READINESS",
            "kubernetesVersion": "string",
            "lastRefreshTime": "timestamp",
            "lastTransitionTime": "timestamp",
            "description": "string",
            "insightStatus": {
                "status": "PASSING|WARNING|ERROR|UNKNOWN",
                "reason": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
