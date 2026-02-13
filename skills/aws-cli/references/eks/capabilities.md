# Capabilities

### 9.1 `describe-cluster-versions`

Lists available Kubernetes versions for EKS clusters.

**Synopsis:**
```bash
aws eks describe-cluster-versions \
    [--cluster-type <value>] \
    [--default-only | --no-default-only] \
    [--include-all | --no-include-all] \
    [--cluster-versions-only <value>] \
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
| `--cluster-type` | No | string | None | Filter by cluster type |
| `--default-only` | No | boolean | false | Only return default version |
| `--include-all` | No | boolean | false | Include all versions including deprecated |
| `--cluster-versions-only` | No | list(string) | None | Specific versions to describe |
| `--status` | No | string | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "clusterVersions": [
        {
            "clusterVersion": "string",
            "clusterType": "string",
            "defaultPlatformVersion": "string",
            "defaultVersion": true|false,
            "releaseDate": "timestamp",
            "endOfStandardSupportDate": "timestamp",
            "endOfExtendedSupportDate": "timestamp",
            "status": "string",
            "kubernetesPatchVersion": "string"
        }
    ],
    "nextToken": "string"
}
```
