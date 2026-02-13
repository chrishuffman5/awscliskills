# Resource Sets

Commands for managing Route 53 ARC resource sets via `aws route53-recovery-readiness`. A resource set is a collection of AWS resources of the same type that are monitored by readiness checks.

### 8.1 `create-resource-set`

Creates a resource set containing resources to monitor for readiness.

**Synopsis:**
```bash
aws route53-recovery-readiness create-resource-set \
    --resource-set-name <value> \
    --resource-set-type <value> \
    --resources <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-set-name` | **Yes** | string | -- | Name of the resource set (max 64 chars) |
| `--resource-set-type` | **Yes** | string | -- | AWS resource type (e.g., `AWS::ElasticLoadBalancingV2::LoadBalancer`) |
| `--resources` | **Yes** | list | -- | List of resource objects |
| `--tags` | No | map | None | Tags as key-value pairs |

**Supported Resource Types:**
- `AWS::ApiGateway::Stage`
- `AWS::AutoScaling::AutoScalingGroup`
- `AWS::CloudWatch::Alarm`
- `AWS::DynamoDB::Table`
- `AWS::EC2::CustomerGateway`
- `AWS::EC2::Volume`
- `AWS::ElasticLoadBalancingV2::LoadBalancer`
- `AWS::Lambda::Function`
- `AWS::MSK::Cluster`
- `AWS::RDS::DBCluster`
- `AWS::Route53::HealthCheck`
- `AWS::SNS::Topic`
- `AWS::SQS::Queue`

**Resource Structure (JSON):**
```json
[
    {
        "ResourceArn": "string",
        "ReadinessScopes": ["cell-arn"],
        "ComponentId": "string",
        "DnsTargetResource": {
            "DomainName": "string",
            "HostedZoneArn": "string",
            "RecordSetId": "string",
            "RecordType": "string",
            "TargetResource": {
                "NLBResource": {
                    "Arn": "string"
                },
                "R53Resource": {
                    "DomainName": "string",
                    "RecordSetId": "string"
                }
            }
        }
    }
]
```

**Output Schema:**
```json
{
    "ResourceSetArn": "string",
    "ResourceSetName": "string",
    "ResourceSetType": "string",
    "Resources": [
        {
            "ComponentId": "string",
            "DnsTargetResource": {
                "DomainName": "string",
                "HostedZoneArn": "string",
                "RecordSetId": "string",
                "RecordType": "string",
                "TargetResource": {
                    "NLBResource": {
                        "Arn": "string"
                    },
                    "R53Resource": {
                        "DomainName": "string",
                        "RecordSetId": "string"
                    }
                }
            },
            "ReadinessScopes": ["string"],
            "ResourceArn": "string"
        }
    ],
    "Tags": {
        "string": "string"
    }
}
```

---

### 8.2 `get-resource-set`

Gets details about a resource set.

**Synopsis:**
```bash
aws route53-recovery-readiness get-resource-set \
    --resource-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-set-name` | **Yes** | string | -- | Name of the resource set |

**Output Schema:** Same as `create-resource-set`.

---

### 8.3 `update-resource-set`

Updates a resource set.

**Synopsis:**
```bash
aws route53-recovery-readiness update-resource-set \
    --resource-set-name <value> \
    --resource-set-type <value> \
    --resources <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-set-name` | **Yes** | string | -- | Name of the resource set |
| `--resource-set-type` | **Yes** | string | -- | AWS resource type |
| `--resources` | **Yes** | list | -- | Updated list of resource objects |

**Output Schema:** Same as `create-resource-set`.

---

### 8.4 `delete-resource-set`

Deletes a resource set.

**Synopsis:**
```bash
aws route53-recovery-readiness delete-resource-set \
    --resource-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-set-name` | **Yes** | string | -- | Name of the resource set to delete |

**Output:** None on success.

---

### 8.5 `list-resource-sets`

Lists all resource sets. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness list-resource-sets \
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
    "ResourceSets": [
        {
            "ResourceSetArn": "string",
            "ResourceSetName": "string",
            "ResourceSetType": "string",
            "Resources": ["..."],
            "Tags": {
                "string": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 8.6 `list-rules`

Lists all readiness rules. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness list-rules \
    [--resource-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | No | string | None | Filter rules by resource type |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Rules": [
        {
            "ResourceType": "string",
            "RuleDescription": "string",
            "RuleId": "string"
        }
    ],
    "NextToken": "string"
}
```
