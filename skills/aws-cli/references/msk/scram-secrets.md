# SCRAM Secrets

## 7.1 `batch-associate-scram-secret`

Associates one or more AWS Secrets Manager SCRAM secrets with an MSK cluster for SASL/SCRAM authentication.

**Synopsis:**
```bash
aws kafka batch-associate-scram-secret \
    --cluster-arn <value> \
    --secret-arn-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--secret-arn-list` | **Yes** | list(string) | -- | List of Secrets Manager secret ARNs (secret names must start with `AmazonMSK_`) |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "UnprocessedScramSecrets": [
        {
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "SecretArn": "string"
        }
    ]
}
```

---

## 7.2 `batch-disassociate-scram-secret`

Disassociates one or more SCRAM secrets from an MSK cluster.

**Synopsis:**
```bash
aws kafka batch-disassociate-scram-secret \
    --cluster-arn <value> \
    --secret-arn-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--secret-arn-list` | **Yes** | list(string) | -- | List of Secrets Manager secret ARNs to disassociate |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "UnprocessedScramSecrets": [
        {
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "SecretArn": "string"
        }
    ]
}
```

---

## 7.3 `list-scram-secrets`

Lists the SCRAM secrets associated with a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-scram-secrets \
    --cluster-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SecretArnList": ["string"],
    "NextToken": "string"
}
```
