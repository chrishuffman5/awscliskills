# Attacks

### 3.1 `describe-attack`

Describes the details of a DDoS attack detected by Shield Advanced.

**Synopsis:**
```bash
aws shield describe-attack \
    --attack-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attack-id` | **Yes** | string | -- | Unique attack identifier (1-128 chars) |

**Output Schema:**
```json
{
    "Attack": {
        "AttackId": "string",
        "ResourceArn": "string",
        "SubResources": [
            {
                "Type": "IP|URL",
                "Id": "string",
                "AttackVectors": [
                    {
                        "VectorType": "string",
                        "VectorCounters": [
                            {
                                "Name": "string",
                                "Max": "double",
                                "Average": "double",
                                "Sum": "double",
                                "N": "integer",
                                "Unit": "string"
                            }
                        ]
                    }
                ],
                "Counters": []
            }
        ],
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "AttackCounters": [
            {
                "Name": "string",
                "Max": "double",
                "Average": "double",
                "Sum": "double",
                "N": "integer",
                "Unit": "string"
            }
        ],
        "AttackProperties": [
            {
                "AttackLayer": "NETWORK|APPLICATION",
                "AttackPropertyIdentifier": "DESTINATION_URL|REFERRER|SOURCE_ASN|SOURCE_COUNTRY|SOURCE_IP_ADDRESS|SOURCE_USER_AGENT|WORDPRESS_PINGBACK_REFLECTOR|WORDPRESS_PINGBACK_SOURCE",
                "TopContributors": [
                    {
                        "Name": "string",
                        "Value": "long"
                    }
                ],
                "Unit": "BITS|BYTES|PACKETS|REQUESTS",
                "Total": "long"
            }
        ],
        "Mitigations": [
            {
                "MitigationName": "string"
            }
        ]
    }
}
```

---

### 3.2 `describe-attack-statistics`

Provides information about the number and type of attacks Shield has detected in the last year. Must be called from the account that is the Shield Advanced subscriber.

**Synopsis:**
```bash
aws shield describe-attack-statistics \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "TimeRange": {
        "FromInclusive": "timestamp",
        "ToExclusive": "timestamp"
    },
    "DataItems": [
        {
            "AttackVolume": {
                "BitsPerSecond": {
                    "Max": "double"
                },
                "PacketsPerSecond": {
                    "Max": "double"
                },
                "RequestsPerSecond": {
                    "Max": "double"
                }
            },
            "AttackCount": "long"
        }
    ]
}
```

---

### 3.3 `list-attacks`

Returns a list of all attacks detected by Shield Advanced within a specified time range. **Paginated.**

**Synopsis:**
```bash
aws shield list-attacks \
    [--resource-arns <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | No | list(string) | None | Filter by resource ARNs |
| `--start-time` | No | structure | None | Start of time range. Shorthand: `FromInclusive=timestamp,ToExclusive=timestamp` |
| `--end-time` | No | structure | None | End of time range. Shorthand: `FromInclusive=timestamp,ToExclusive=timestamp` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AttackSummaries": [
        {
            "AttackId": "string",
            "ResourceArn": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "AttackVectors": [
                {
                    "VectorType": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
