# Clusters

### 2.1 `create-cluster`

Creates a cluster of Snow Family devices. Each cluster supports up to 16 nodes. Cluster jobs use `LOCAL_USE` job type for edge computing workloads.

**Synopsis:**
```bash
aws snowball create-cluster \
    --job-type <value> \
    --address-id <value> \
    --snowball-type <value> \
    --shipping-option <value> \
    [--resources <value>] \
    [--on-device-service-configuration <value>] \
    [--description <value>] \
    [--kms-key-arn <value>] \
    [--role-arn <value>] \
    [--notification <value>] \
    [--forwarding-address-id <value>] \
    [--tax-documents <value>] \
    [--remote-management <value>] \
    [--initial-cluster-size <value>] \
    [--force-create-jobs | --no-force-create-jobs] \
    [--long-term-pricing-ids <value>] \
    [--snowball-capacity-preference <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-type` | **Yes** | string | -- | Job type: `IMPORT`, `EXPORT`, `LOCAL_USE` (clusters typically use `LOCAL_USE`) |
| `--address-id` | **Yes** | string | -- | Address ID for cluster shipment (40 chars) |
| `--snowball-type` | **Yes** | string | -- | Device type: `STANDARD`, `EDGE`, `EDGE_C`, `EDGE_CG`, `EDGE_S`, `SNC1_HDD`, `SNC1_SSD`, `V3_5C`, `V3_5S`, `RACK_5U_C` |
| `--shipping-option` | **Yes** | string | -- | Shipping speed: `SECOND_DAY`, `NEXT_DAY`, `EXPRESS`, `STANDARD` |
| `--resources` | No | structure | None | S3, Lambda, and EC2 AMI resources |
| `--on-device-service-configuration` | No | structure | None | On-device services: NFS, Tape Gateway, EKS, S3 |
| `--description` | No | string | None | Cluster description (1-1024 chars) |
| `--kms-key-arn` | No | string | None | KMS key ARN for encryption |
| `--role-arn` | No | string | None | IAM role ARN (max 255 chars) |
| `--notification` | No | structure | None | SNS notification settings |
| `--forwarding-address-id` | No | string | None | Forwarding address ID (40 chars) |
| `--tax-documents` | No | structure | None | Tax documents (India: GSTIN) |
| `--remote-management` | No | string | None | Remote management: `INSTALLED_ONLY`, `INSTALLED_AUTOSTART`, `NOT_INSTALLED` |
| `--initial-cluster-size` | No | integer | None | Number of jobs to auto-create (0-16) |
| `--force-create-jobs` | No | boolean | None | Force cluster creation despite over/under-provisioning |
| `--long-term-pricing-ids` | No | list(string) | None | Long-term pricing IDs for auto-created jobs |
| `--snowball-capacity-preference` | No | string | None | Preferred device capacity (US regions only) |

**Output Schema:**
```json
{
    "ClusterId": "string",
    "JobListEntries": [
        {
            "JobId": "string",
            "JobState": "New|PreparingAppliance|PreparingShipment|InTransitToCustomer|WithCustomer|InTransitToAWS|WithAWSSortingFacility|WithAWS|InProgress|Complete|Cancelled|Listing|Pending",
            "IsMaster": "boolean",
            "JobType": "IMPORT|EXPORT|LOCAL_USE",
            "SnowballType": "string",
            "CreationDate": "timestamp",
            "Description": "string"
        }
    ]
}
```

---

### 2.2 `describe-cluster`

Returns information about a specific cluster, including its current state, type, and associated resources.

**Synopsis:**
```bash
aws snowball describe-cluster \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID (39 chars, pattern: `CID...`) |

**Output Schema:**
```json
{
    "ClusterMetadata": {
        "ClusterId": "string",
        "Description": "string",
        "KmsKeyARN": "string",
        "RoleARN": "string",
        "ClusterState": "AwaitingQuorum|Pending|InUse|Complete|Cancelled",
        "JobType": "IMPORT|EXPORT|LOCAL_USE",
        "SnowballType": "STANDARD|EDGE|EDGE_C|EDGE_CG|EDGE_S|SNC1_HDD|SNC1_SSD|V3_5C|V3_5S|RACK_5U_C",
        "CreationDate": "timestamp",
        "Resources": {
            "S3Resources": [
                {
                    "BucketArn": "string",
                    "KeyRange": {
                        "BeginMarker": "string",
                        "EndMarker": "string"
                    },
                    "TargetOnDeviceServices": [
                        {
                            "ServiceName": "NFS_ON_DEVICE_SERVICE|S3_ON_DEVICE_SERVICE",
                            "TransferOption": "IMPORT|EXPORT|LOCAL_USE"
                        }
                    ]
                }
            ],
            "LambdaResources": [],
            "Ec2AmiResources": []
        },
        "AddressId": "string",
        "ShippingOption": "SECOND_DAY|NEXT_DAY|EXPRESS|STANDARD",
        "Notification": {
            "SnsTopicARN": "string",
            "JobStatesToNotify": ["string"],
            "NotifyAll": "boolean",
            "DevicePickupSnsTopicARN": "string"
        },
        "ForwardingAddressId": "string",
        "TaxDocuments": {
            "IND": {
                "GSTIN": "string"
            }
        },
        "OnDeviceServiceConfiguration": {
            "NFSOnDeviceService": {
                "StorageLimit": "integer",
                "StorageUnit": "TB"
            },
            "TGWOnDeviceService": {
                "StorageLimit": "integer",
                "StorageUnit": "TB"
            },
            "EKSOnDeviceService": {
                "KubernetesVersion": "string",
                "EKSAnywhereVersion": "string"
            },
            "S3OnDeviceService": {
                "StorageLimit": "double",
                "StorageUnit": "TB",
                "ServiceSize": "integer",
                "FaultTolerance": "integer"
            }
        }
    }
}
```

---

### 2.3 `update-cluster`

Updates an existing cluster. Only available while the cluster's `ClusterState` is `AwaitingQuorum` (typically within 60 minutes of creation).

**Synopsis:**
```bash
aws snowball update-cluster \
    --cluster-id <value> \
    [--role-arn <value>] \
    [--description <value>] \
    [--resources <value>] \
    [--on-device-service-configuration <value>] \
    [--address-id <value>] \
    [--shipping-option <value>] \
    [--notification <value>] \
    [--forwarding-address-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID to update (39 chars) |
| `--role-arn` | No | string | None | New IAM role ARN (max 255 chars) |
| `--description` | No | string | None | Updated description (1-1024 chars) |
| `--resources` | No | structure | None | Updated S3, Lambda, or EC2 AMI resources |
| `--on-device-service-configuration` | No | structure | None | Updated on-device service configuration |
| `--address-id` | No | string | None | Updated address ID (40 chars) |
| `--shipping-option` | No | string | None | Updated shipping speed: `SECOND_DAY`, `NEXT_DAY`, `EXPRESS`, `STANDARD` |
| `--notification` | No | structure | None | Updated SNS notification settings |
| `--forwarding-address-id` | No | string | None | Updated forwarding address ID (40 chars) |

**Output:** None

---

### 2.4 `cancel-cluster`

Cancels a cluster job. Can only cancel while the cluster is in the `AwaitingQuorum` state. At least one hour is available after creation to cancel.

**Synopsis:**
```bash
aws snowball cancel-cluster \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID to cancel (39 chars) |

**Output:** None

---

### 2.5 `list-clusters`

Returns an array of `ClusterListEntry` objects for all clusters in the account. **Paginated operation.**

**Synopsis:**
```bash
aws snowball list-clusters \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ClusterListEntries": [
        {
            "ClusterId": "string",
            "ClusterState": "AwaitingQuorum|Pending|InUse|Complete|Cancelled",
            "CreationDate": "timestamp",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `list-cluster-jobs`

Returns an array of `JobListEntry` objects for all jobs associated with a specific cluster. **Paginated operation.**

**Synopsis:**
```bash
aws snowball list-cluster-jobs \
    --cluster-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID (39 chars) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "JobListEntries": [
        {
            "JobId": "string",
            "JobState": "New|PreparingAppliance|PreparingShipment|InTransitToCustomer|WithCustomer|InTransitToAWS|WithAWSSortingFacility|WithAWS|InProgress|Complete|Cancelled|Listing|Pending",
            "IsMaster": "boolean",
            "JobType": "IMPORT|EXPORT|LOCAL_USE",
            "SnowballType": "string",
            "CreationDate": "timestamp",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```
