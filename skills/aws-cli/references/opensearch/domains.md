# Domains

### 1.1 `create-domain`

Creates an Amazon OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch create-domain \
    --domain-name <value> \
    [--engine-version <value>] \
    [--cluster-config <value>] \
    [--ebs-options <value>] \
    [--access-policies <value>] \
    [--ip-address-type <value>] \
    [--vpc-options <value>] \
    [--cognito-options <value>] \
    [--encryption-at-rest-options <value>] \
    [--node-to-node-encryption-options <value>] \
    [--advanced-options <value>] \
    [--log-publishing-options <value>] \
    [--domain-endpoint-options <value>] \
    [--advanced-security-options <value>] \
    [--auto-tune-options <value>] \
    [--off-peak-window-options <value>] \
    [--software-update-options <value>] \
    [--aiml-options <value>] \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (3-28 chars, pattern: `[a-z][a-z0-9\-]+`) |
| `--engine-version` | No | string | latest | Engine version (e.g., `OpenSearch_2.11`, `Elasticsearch_7.10`) |
| `--cluster-config` | No | structure | None | Instance type, count, master nodes, zones, warm/cold storage |
| `--ebs-options` | No | structure | None | EBS volume type, size, IOPS, throughput |
| `--access-policies` | No | string | None | IAM resource-based policy document (JSON) |
| `--ip-address-type` | No | string | `ipv4` | `ipv4` or `dualstack` |
| `--vpc-options` | No | structure | None | VPC subnet IDs and security group IDs |
| `--cognito-options` | No | structure | None | Cognito authentication for Dashboards |
| `--encryption-at-rest-options` | No | structure | None | Encryption at rest with KMS key |
| `--node-to-node-encryption-options` | No | structure | None | Node-to-node encryption |
| `--advanced-options` | No | map | None | Advanced configuration options |
| `--log-publishing-options` | No | map | None | CloudWatch log publishing |
| `--domain-endpoint-options` | No | structure | None | HTTPS enforcement, TLS policy, custom endpoints |
| `--advanced-security-options` | No | structure | None | Fine-grained access control, SAML, JWT |
| `--auto-tune-options` | No | structure | None | Auto-Tune settings |
| `--off-peak-window-options` | No | structure | None | Off-peak maintenance window |
| `--software-update-options` | No | structure | None | Auto software updates |
| `--aiml-options` | No | structure | None | ML features configuration |
| `--tag-list` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Cluster Config Structure:**
```json
{
    "InstanceType": "r6g.large.search",
    "InstanceCount": 3,
    "DedicatedMasterEnabled": true,
    "DedicatedMasterType": "r6g.large.search",
    "DedicatedMasterCount": 3,
    "ZoneAwarenessEnabled": true,
    "ZoneAwarenessConfig": {"AvailabilityZoneCount": 3},
    "WarmEnabled": false,
    "ColdStorageOptions": {"Enabled": false},
    "MultiAZWithStandbyEnabled": false
}
```

**EBS Options Structure:**
```json
{
    "EBSEnabled": true,
    "VolumeType": "gp3",
    "VolumeSize": 100,
    "Iops": 3000,
    "Throughput": 125
}
```

**Output Schema:**
```json
{
    "DomainStatus": {
        "DomainId": "string",
        "DomainName": "string",
        "ARN": "string",
        "Created": "boolean",
        "Deleted": "boolean",
        "Endpoint": "string",
        "EndpointV2": "string",
        "Processing": "boolean",
        "UpgradeProcessing": "boolean",
        "EngineVersion": "string",
        "ClusterConfig": {},
        "EBSOptions": {},
        "AccessPolicies": "string",
        "VPCOptions": {},
        "EncryptionAtRestOptions": {},
        "NodeToNodeEncryptionOptions": {},
        "AdvancedSecurityOptions": {},
        "DomainEndpointOptions": {},
        "AutoTuneOptions": {},
        "DomainProcessingStatus": "Creating|Active|Modifying|Deleting"
    }
}
```

---

### 1.2 `delete-domain`

Deletes an OpenSearch Service domain and all of its data.

**Synopsis:**
```bash
aws opensearch delete-domain \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain to delete |

**Output Schema:**
```json
{
    "DomainStatus": {
        "DomainId": "string",
        "DomainName": "string",
        "ARN": "string",
        "Deleted": true,
        "DomainProcessingStatus": "Deleting"
    }
}
```

---

### 1.3 `describe-domain`

Returns details about a single domain.

**Synopsis:**
```bash
aws opensearch describe-domain \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "DomainStatus": {
        "DomainId": "string",
        "DomainName": "string",
        "ARN": "string",
        "Created": "boolean",
        "Deleted": "boolean",
        "Endpoint": "string",
        "EndpointV2": "string",
        "Processing": "boolean",
        "UpgradeProcessing": "boolean",
        "EngineVersion": "string",
        "ClusterConfig": {
            "InstanceType": "string",
            "InstanceCount": "integer",
            "DedicatedMasterEnabled": "boolean",
            "DedicatedMasterType": "string",
            "DedicatedMasterCount": "integer",
            "ZoneAwarenessEnabled": "boolean",
            "WarmEnabled": "boolean",
            "WarmType": "string",
            "WarmCount": "integer",
            "ColdStorageOptions": {"Enabled": "boolean"}
        },
        "EBSOptions": {
            "EBSEnabled": "boolean",
            "VolumeType": "string",
            "VolumeSize": "integer",
            "Iops": "integer",
            "Throughput": "integer"
        },
        "AccessPolicies": "string",
        "VPCOptions": {
            "VPCId": "string",
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "EncryptionAtRestOptions": {"Enabled": "boolean", "KmsKeyId": "string"},
        "NodeToNodeEncryptionOptions": {"Enabled": "boolean"},
        "AdvancedSecurityOptions": {"Enabled": "boolean", "InternalUserDatabaseEnabled": "boolean"},
        "DomainEndpointOptions": {
            "EnforceHTTPS": "boolean",
            "TLSSecurityPolicy": "string",
            "CustomEndpointEnabled": "boolean"
        },
        "ServiceSoftwareOptions": {
            "CurrentVersion": "string",
            "NewVersion": "string",
            "UpdateAvailable": "boolean",
            "UpdateStatus": "PENDING_UPDATE|IN_PROGRESS|COMPLETED|NOT_ELIGIBLE|ELIGIBLE"
        },
        "AutoTuneOptions": {"State": "string"},
        "DomainProcessingStatus": "string"
    }
}
```

---

### 1.4 `describe-domains`

Returns details about multiple domains.

**Synopsis:**
```bash
aws opensearch describe-domains \
    --domain-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-names` | **Yes** | list(string) | -- | List of domain names (max 5) |

**Output Schema:**
```json
{
    "DomainStatusList": [
        {
            "DomainId": "string",
            "DomainName": "string",
            "ARN": "string",
            "EngineVersion": "string",
            "ClusterConfig": {},
            "DomainProcessingStatus": "string"
        }
    ]
}
```

---

### 1.5 `describe-domain-config`

Returns the full configuration for a domain.

**Synopsis:**
```bash
aws opensearch describe-domain-config \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "DomainConfig": {
        "EngineVersion": {"Options": "string", "Status": {}},
        "ClusterConfig": {"Options": {}, "Status": {}},
        "EBSOptions": {"Options": {}, "Status": {}},
        "AccessPolicies": {"Options": "string", "Status": {}},
        "VPCOptions": {"Options": {}, "Status": {}},
        "EncryptionAtRestOptions": {"Options": {}, "Status": {}},
        "NodeToNodeEncryptionOptions": {"Options": {}, "Status": {}},
        "AdvancedSecurityOptions": {"Options": {}, "Status": {}},
        "DomainEndpointOptions": {"Options": {}, "Status": {}},
        "AutoTuneOptions": {"Options": {}, "Status": {}}
    }
}
```

---

### 1.6 `update-domain-config`

Modifies the configuration of a domain. Accepts all the same configuration parameters as `create-domain`.

**Synopsis:**
```bash
aws opensearch update-domain-config \
    --domain-name <value> \
    [--cluster-config <value>] \
    [--ebs-options <value>] \
    [--access-policies <value>] \
    [--vpc-options <value>] \
    [--cognito-options <value>] \
    [--encryption-at-rest-options <value>] \
    [--node-to-node-encryption-options <value>] \
    [--advanced-options <value>] \
    [--log-publishing-options <value>] \
    [--domain-endpoint-options <value>] \
    [--advanced-security-options <value>] \
    [--auto-tune-options <value>] \
    [--off-peak-window-options <value>] \
    [--software-update-options <value>] \
    [--aiml-options <value>] \
    [--ip-address-type <value>] \
    [--dry-run | --no-dry-run] \
    [--dry-run-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |
| `--dry-run` | No | boolean | false | Validate changes without applying |
| `--dry-run-mode` | No | string | -- | `Basic` or `Verbose` dry-run mode |
| *(all config params)* | No | *(various)* | -- | Same as `create-domain` configuration parameters |

**Output Schema:**
```json
{
    "DomainConfig": {},
    "DryRunResults": {
        "DeploymentType": "string",
        "Message": "string"
    },
    "DryRunProgressStatus": {
        "DryRunId": "string",
        "DryRunStatus": "string"
    }
}
```

---

### 1.7 `list-domain-names`

Lists all domain names in the account.

**Synopsis:**
```bash
aws opensearch list-domain-names \
    [--engine-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine-type` | No | string | -- | Filter by engine: `OpenSearch` or `Elasticsearch` |

**Output Schema:**
```json
{
    "DomainNames": [
        {
            "DomainName": "string",
            "EngineType": "OpenSearch|Elasticsearch"
        }
    ]
}
```

---

### 1.8 `describe-domain-health`

Returns health information about a domain.

**Synopsis:**
```bash
aws opensearch describe-domain-health \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "DomainState": "Active|Processing|NotAvailable",
    "AvailabilityZoneCount": "string",
    "ActiveAvailabilityZoneCount": "string",
    "StandByAvailabilityZoneCount": "string",
    "DataNodeCount": "string",
    "DedicatedMaster": "boolean",
    "MasterEligibleNodeCount": "string",
    "WarmNodeCount": "string",
    "MasterNode": {
        "AvailabilityZone": "string",
        "InstanceType": "string",
        "NodeId": "string",
        "NodeStatus": "Active|StandBy|NotAvailable"
    },
    "ClusterHealth": "Red|Yellow|Green|NotAvailable",
    "TotalShards": "string",
    "TotalUnAssignedShards": "string",
    "EnvironmentInformation": []
}
```

---

### 1.9 `describe-domain-nodes`

Returns information about nodes in a domain.

**Synopsis:**
```bash
aws opensearch describe-domain-nodes \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "DomainNodesStatusList": [
        {
            "NodeId": "string",
            "NodeType": "Data|Ultrawarm|Master",
            "AvailabilityZone": "string",
            "InstanceType": "string",
            "NodeStatus": "Active|StandBy|NotAvailable",
            "StorageType": "string",
            "StorageVolumeType": "string",
            "StorageSize": "string"
        }
    ]
}
```

---

### 1.10 `describe-domain-auto-tunes`

Returns Auto-Tune settings and status for a domain. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch describe-domain-auto-tunes \
    --domain-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "AutoTunes": [
        {
            "AutoTuneType": "SCHEDULED_ACTION",
            "AutoTuneDetails": {
                "ScheduledAutoTuneDetails": {
                    "Date": "timestamp",
                    "ActionType": "JVM_HEAP_SIZE_TUNING|JVM_YOUNG_GEN_TUNING",
                    "Action": "string",
                    "Severity": "LOW|MEDIUM|HIGH"
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.11 `describe-domain-change-progress`

Returns progress information for a domain configuration change.

**Synopsis:**
```bash
aws opensearch describe-domain-change-progress \
    --domain-name <value> \
    [--change-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |
| `--change-id` | No | string | -- | Specific change ID (defaults to most recent) |

**Output Schema:**
```json
{
    "ChangeProgressStatus": {
        "ChangeId": "string",
        "StartTime": "timestamp",
        "Status": "PENDING|PROCESSING|COMPLETED|FAILED",
        "PendingProperties": ["string"],
        "CompletedProperties": ["string"],
        "TotalNumberOfStages": "integer",
        "ChangeProgressStages": [
            {
                "Name": "string",
                "Status": "string",
                "Description": "string",
                "LastUpdated": "timestamp"
            }
        ],
        "LastUpdatedTime": "timestamp",
        "ConfigChangeStatus": "Pending|Initializing|Validating|ApplyingChanges|Completed|Cancelled",
        "InitiatedBy": "CUSTOMER|SERVICE"
    }
}
```

---

### 1.12 `cancel-domain-config-change`

Cancels a pending configuration change on a domain.

**Synopsis:**
```bash
aws opensearch cancel-domain-config-change \
    --domain-name <value> \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |
| `--dry-run` | No | boolean | false | Validate without cancelling |

**Output Schema:**
```json
{
    "DryRun": "boolean",
    "CancelledChangeIds": ["string"],
    "CancelledChangeProperties": [
        {
            "PropertyName": "string",
            "CancelledValue": "string",
            "ActiveValue": "string"
        }
    ]
}
```

---

### 1.13 `describe-instance-type-limits`

Returns instance type limits for a given engine version.

**Synopsis:**
```bash
aws opensearch describe-instance-type-limits \
    --instance-type <value> \
    --engine-version <value> \
    [--domain-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-type` | **Yes** | string | -- | Instance type (e.g., `r6g.large.search`) |
| `--engine-version` | **Yes** | string | -- | Engine version (e.g., `OpenSearch_2.11`) |
| `--domain-name` | No | string | -- | Domain for domain-specific limits |

**Output Schema:**
```json
{
    "LimitsByRole": {
        "data": {
            "StorageTypes": [
                {
                    "StorageTypeName": "string",
                    "StorageSubTypeName": "string",
                    "StorageTypeLimits": []
                }
            ],
            "InstanceLimits": {
                "InstanceCountLimits": {
                    "MinimumInstanceCount": "integer",
                    "MaximumInstanceCount": "integer"
                }
            },
            "AdditionalLimits": []
        },
        "master": {}
    }
}
```

---

### 1.14 `list-instance-type-details`

Lists instance types available for a given engine version. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch list-instance-type-details \
    --engine-version <value> \
    [--domain-name <value>] \
    [--instance-type <value>] \
    [--retrieve-a-zs | --no-retrieve-a-zs] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine-version` | **Yes** | string | -- | Engine version |
| `--domain-name` | No | string | -- | Domain name for domain-specific info |
| `--instance-type` | No | string | -- | Filter by instance type |
| `--retrieve-a-zs` | No | boolean | false | Include availability zone info |

**Output Schema:**
```json
{
    "InstanceTypeDetails": [
        {
            "InstanceType": "string",
            "EncryptionEnabled": "boolean",
            "CognitoEnabled": "boolean",
            "AppLogsEnabled": "boolean",
            "AdvancedSecurityEnabled": "boolean",
            "WarmEnabled": "boolean",
            "InstanceRole": ["string"],
            "AvailabilityZones": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 1.15 `get-compatible-versions`

Returns compatible engine versions for an upgrade.

**Synopsis:**
```bash
aws opensearch get-compatible-versions \
    [--domain-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | No | string | -- | Domain name (returns domain-specific compatibility) |

**Output Schema:**
```json
{
    "CompatibleVersions": [
        {
            "SourceVersion": "string",
            "TargetVersions": ["string"]
        }
    ]
}
```

---

### 1.16 `list-versions`

Lists all available OpenSearch and Elasticsearch engine versions. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch list-versions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Versions": ["string"],
    "NextToken": "string"
}
```

---

### 1.17 `describe-reserved-instances`

Lists reserved instances. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch describe-reserved-instances \
    [--reserved-instance-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-instance-id` | No | string | -- | Specific reservation ID |

**Output Schema:**
```json
{
    "ReservedInstances": [
        {
            "ReservedInstanceId": "string",
            "ReservedInstanceOfferingId": "string",
            "InstanceType": "string",
            "InstanceCount": "integer",
            "State": "string",
            "PaymentOption": "ALL_UPFRONT|PARTIAL_UPFRONT|NO_UPFRONT",
            "Duration": "integer",
            "FixedPrice": "double",
            "UsagePrice": "double",
            "StartTime": "timestamp",
            "BillingSubscriptionId": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.18 `describe-reserved-instance-offerings`

Lists available reserved instance offerings. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch describe-reserved-instance-offerings \
    [--reserved-instance-offering-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "ReservedInstanceOfferings": [
        {
            "ReservedInstanceOfferingId": "string",
            "InstanceType": "string",
            "Duration": "integer",
            "FixedPrice": "double",
            "UsagePrice": "double",
            "CurrencyCode": "string",
            "PaymentOption": "ALL_UPFRONT|PARTIAL_UPFRONT|NO_UPFRONT",
            "RecurringCharges": []
        }
    ],
    "NextToken": "string"
}
```

---

### 1.19 `purchase-reserved-instance-offering`

Purchases a reserved instance offering.

**Synopsis:**
```bash
aws opensearch purchase-reserved-instance-offering \
    --reserved-instance-offering-id <value> \
    --reservation-name <value> \
    [--instance-count <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-instance-offering-id` | **Yes** | string | -- | Offering ID to purchase |
| `--reservation-name` | **Yes** | string | -- | Name for the reservation |
| `--instance-count` | No | integer | 1 | Number of instances to reserve |

**Output Schema:**
```json
{
    "ReservedInstanceId": "string",
    "ReservationName": "string"
}
```
