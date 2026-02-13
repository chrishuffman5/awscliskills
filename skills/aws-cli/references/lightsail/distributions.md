# Distributions

### 7.1 `create-distribution`

Creates a Lightsail CDN distribution.

**Synopsis:**
```bash
aws lightsail create-distribution \
    --distribution-name <value> \
    --origin <value> \
    --default-cache-behavior <value> \
    --bundle-id <value> \
    [--cache-behavior-settings <value>] \
    [--cache-behaviors <value>] \
    [--ip-address-type <value>] \
    [--tags <value>] \
    [--certificate-name <value>] \
    [--viewer-minimum-tls-protocol-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | **Yes** | string | -- | Name for the distribution |
| `--origin` | **Yes** | structure | -- | Origin resource. Shorthand: `name=string,regionName=string,protocolPolicy=http-only\|https-only` |
| `--default-cache-behavior` | **Yes** | structure | -- | Default cache behavior. Shorthand: `behavior=dont-cache\|cache` |
| `--bundle-id` | **Yes** | string | -- | Bundle ID (e.g., `small_1_0`, `medium_1_0`, `large_1_0`) |
| `--cache-behavior-settings` | No | structure | None | Cache behavior settings (TTL, allowed methods, forwarded values) |
| `--cache-behaviors` | No | list | None | Path-specific cache behaviors |
| `--ip-address-type` | No | string | `dualstack` | IP address type: `dualstack`, `ipv4`, `ipv6` |
| `--tags` | No | list | None | Tags |
| `--certificate-name` | No | string | None | Certificate for custom domain |
| `--viewer-minimum-tls-protocol-version` | No | string | None | Minimum TLS version: `TLSv1.1_2016`, `TLSv1.2_2018`, `TLSv1.2_2019`, `TLSv1.2_2021` |

**Output Schema:**
```json
{
    "distribution": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "Distribution",
        "alternativeDomainNames": ["string"],
        "status": "string",
        "isEnabled": true|false,
        "domainName": "string",
        "bundleId": "string",
        "certificateName": "string",
        "origin": {
            "name": "string",
            "resourceType": "string",
            "regionName": "string",
            "protocolPolicy": "http-only|https-only"
        },
        "originPublicDNS": "string",
        "defaultCacheBehavior": {
            "behavior": "dont-cache|cache"
        },
        "cacheBehaviorSettings": {
            "defaultTTL": "long",
            "minimumTTL": "long",
            "maximumTTL": "long",
            "allowedHTTPMethods": "string",
            "cachedHTTPMethods": "string",
            "forwardedCookies": {},
            "forwardedHeaders": {},
            "forwardedQueryStrings": {}
        },
        "cacheBehaviors": [],
        "ableToUpdateBundle": true|false,
        "ipAddressType": "dualstack|ipv4|ipv6",
        "tags": [],
        "viewerMinimumTlsProtocolVersion": "string"
    },
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Distribution",
        "operationType": "CreateDistribution",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 7.2 `delete-distribution`

Deletes a distribution.

**Synopsis:**
```bash
aws lightsail delete-distribution \
    [--distribution-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | No | string | None | Name of the distribution to delete |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Distribution",
        "operationType": "DeleteDistribution",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 7.3 `get-distributions`

Returns information about distributions. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-distributions \
    [--distribution-name <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | No | string | None | Name of a specific distribution |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "distributions": [
        {
            "name": "string",
            "arn": "string",
            "status": "string",
            "isEnabled": true|false,
            "domainName": "string",
            "bundleId": "string",
            "origin": {
                "name": "string",
                "resourceType": "string",
                "regionName": "string",
                "protocolPolicy": "string"
            }
        }
    ],
    "nextPageToken": "string"
}
```

---

### 7.4 `update-distribution`

Updates a distribution configuration.

**Synopsis:**
```bash
aws lightsail update-distribution \
    --distribution-name <value> \
    [--origin <value>] \
    [--default-cache-behavior <value>] \
    [--cache-behavior-settings <value>] \
    [--cache-behaviors <value>] \
    [--is-enabled | --no-is-enabled] \
    [--viewer-minimum-tls-protocol-version <value>] \
    [--certificate-name <value>] \
    [--use-default-certificate | --no-use-default-certificate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | **Yes** | string | -- | Name of the distribution |
| `--origin` | No | structure | None | Origin configuration |
| `--default-cache-behavior` | No | structure | None | Default cache behavior |
| `--cache-behavior-settings` | No | structure | None | Cache behavior settings |
| `--cache-behaviors` | No | list | None | Path-specific cache behaviors |
| `--is-enabled` | No | boolean | None | Enable or disable the distribution |
| `--viewer-minimum-tls-protocol-version` | No | string | None | Minimum TLS version |
| `--certificate-name` | No | string | None | Certificate for custom domain |
| `--use-default-certificate` | No | boolean | None | Use the default certificate |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Distribution",
        "operationType": "UpdateDistribution",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 7.5 `update-distribution-bundle`

Updates the bundle (plan) for a distribution.

**Synopsis:**
```bash
aws lightsail update-distribution-bundle \
    [--distribution-name <value>] \
    [--bundle-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | No | string | None | Name of the distribution |
| `--bundle-id` | No | string | None | New bundle ID |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Distribution",
        "operationType": "UpdateDistributionBundle",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 7.6 `get-distribution-bundles`

Returns available distribution bundles.

**Synopsis:**
```bash
aws lightsail get-distribution-bundles \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "bundles": [
        {
            "bundleId": "string",
            "name": "string",
            "price": "float",
            "transferPerMonthInGb": "integer",
            "isActive": true|false
        }
    ]
}
```

---

### 7.7 `get-distribution-latest-cache-reset`

Returns the timestamp and status of the last cache reset.

**Synopsis:**
```bash
aws lightsail get-distribution-latest-cache-reset \
    [--distribution-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | No | string | None | Name of the distribution |

**Output Schema:**
```json
{
    "status": "string",
    "createTime": "timestamp"
}
```

---

### 7.8 `get-distribution-metric-data`

Returns metric data for a distribution.

**Synopsis:**
```bash
aws lightsail get-distribution-metric-data \
    --distribution-name <value> \
    --metric-name <value> \
    --start-time <value> \
    --end-time <value> \
    --period <value> \
    --unit <value> \
    --statistics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | **Yes** | string | -- | Name of the distribution |
| `--metric-name` | **Yes** | string | -- | Metric: `Requests`, `BytesDownloaded`, `BytesUploaded`, `TotalErrorRate`, `Http4xxErrorRate`, `Http5xxErrorRate` |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |
| `--period` | **Yes** | integer | -- | Granularity in seconds |
| `--unit` | **Yes** | string | -- | Unit for the metric |
| `--statistics` | **Yes** | list(string) | -- | Statistics: `Minimum`, `Maximum`, `Sum`, `Average`, `SampleCount` |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricData": [
        {
            "average": "double",
            "maximum": "double",
            "minimum": "double",
            "sampleCount": "double",
            "sum": "double",
            "timestamp": "timestamp",
            "unit": "string"
        }
    ]
}
```

---

### 7.9 `reset-distribution-cache`

Resets the cache for a distribution.

**Synopsis:**
```bash
aws lightsail reset-distribution-cache \
    [--distribution-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | No | string | None | Name of the distribution |

**Output Schema:**
```json
{
    "status": "string",
    "createTime": "timestamp",
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Distribution",
        "operationType": "ResetDistributionCache",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 7.10 `attach-certificate-to-distribution`

Attaches an SSL/TLS certificate to a distribution.

**Synopsis:**
```bash
aws lightsail attach-certificate-to-distribution \
    --distribution-name <value> \
    --certificate-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | **Yes** | string | -- | Name of the distribution |
| `--certificate-name` | **Yes** | string | -- | Name of the certificate to attach |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Distribution",
        "operationType": "AttachCertificateToDistribution",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 7.11 `detach-certificate-from-distribution`

Detaches a certificate from a distribution.

**Synopsis:**
```bash
aws lightsail detach-certificate-from-distribution \
    --distribution-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-name` | **Yes** | string | -- | Name of the distribution |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Distribution",
        "operationType": "DetachCertificateFromDistribution",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```
