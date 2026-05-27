# Launch Templates

### 6.1 `aws ec2 create-launch-template`

**Description:** Creates a launch template storing instance launch parameters for reuse with RunInstances, Auto Scaling groups, etc.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-template-name` | string | **Required** | Name (3-128 chars, pattern: `[a-zA-Z0-9\(\)\.\-/_]+`) |
| `--launch-template-data` | structure | **Required** | Launch configuration (see below) |
| `--version-description` | string | Optional | Description for version 1 (max 255 chars) |
| `--client-token` | string | Optional | Idempotency token (max 128 chars) |
| `--tag-specifications` | list(structure) | Optional | Tags for the launch template |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

**Launch Template Data Structure (key fields):**

| Field | Type | Description |
|-------|------|-------------|
| `ImageId` | string | AMI ID or SSM parameter reference |
| `InstanceType` | string | Instance type (e.g., `t3.micro`, `m5.large`) |
| `KeyName` | string | Key pair name |
| `SecurityGroupIds` | list(string) | Security group IDs |
| `SecurityGroups` | list(string) | Security group names |
| `UserData` | string | Base64-encoded user data (max 16 KB) |
| `EbsOptimized` | boolean | EBS optimization |
| `IamInstanceProfile` | structure | `{Arn: string}` or `{Name: string}` |
| `Monitoring` | structure | `{Enabled: bool}` |
| `Placement` | structure | `{AvailabilityZone, GroupName, Tenancy, HostId, PartitionNumber}` |
| `BlockDeviceMappings` | list(structure) | Storage configuration |
| `NetworkInterfaces` | list(structure) | Network interface specs (DeviceIndex, SubnetId, Groups, AssociatePublicIpAddress, etc.) |
| `TagSpecifications` | list(structure) | Tags for launched resources |
| `CreditSpecification` | structure | `{CpuCredits: [standard/unlimited]}` |
| `CpuOptions` | structure | `{CoreCount: int, ThreadsPerCore: int}` |
| `MetadataOptions` | structure | `{HttpTokens: [optional/required], HttpPutResponseHopLimit: int, HttpEndpoint: [enabled/disabled]}` |
| `HibernationOptions` | structure | `{Configured: bool}` |
| `EnclaveOptions` | structure | `{Enabled: bool}` |
| `CapacityReservationSpecification` | structure | Capacity Reservation targeting |
| `InstanceMarketOptions` | structure | Spot/capacity-block options |
| `InstanceRequirements` | structure | Attribute-based instance selection |
| `DisableApiTermination` | boolean | Termination protection |
| `DisableApiStop` | boolean | Stop protection |
| `MaintenanceOptions` | structure | Auto-recovery behavior |
| `PrivateDnsNameOptions` | structure | DNS hostname options |

#### Output Schema

```json
{
  "LaunchTemplate": {
    "LaunchTemplateId": "string",
    "LaunchTemplateName": "string",
    "CreateTime": "timestamp",
    "CreatedBy": "string",
    "DefaultVersionNumber": 1,
    "LatestVersionNumber": 1,
    "Tags": [{ "Key": "string", "Value": "string" }]
  }
}
```

---

### 6.2 `aws ec2 delete-launch-template`

**Description:** Deletes a launch template and all its versions.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-template-id` | string | Optional* | Launch template ID |
| `--launch-template-name` | string | Optional* | Launch template name |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

*Must specify one of `--launch-template-id` or `--launch-template-name`.

#### Output Schema

```json
{
  "LaunchTemplate": {
    "LaunchTemplateId": "string",
    "LaunchTemplateName": "string",
    "CreateTime": "timestamp",
    "CreatedBy": "string",
    "DefaultVersionNumber": 0,
    "LatestVersionNumber": 0,
    "Tags": [{ "Key": "string", "Value": "string" }]
  }
}
```

---

### 6.3 `aws ec2 describe-launch-templates`

**Description:** Describes one or more launch templates. Paginated.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-template-ids` | list(string) | Optional | Template IDs |
| `--launch-template-names` | list(string) | Optional | Template names |
| `--filters` | list(structure) | Optional | Filters: `create-time`, `launch-template-name`, `tag:<key>`, `tag-key` |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

#### Output Schema

```json
{
  "LaunchTemplates": [
    {
      "LaunchTemplateId": "string",
      "LaunchTemplateName": "string",
      "CreateTime": "timestamp",
      "CreatedBy": "string",
      "DefaultVersionNumber": 0,
      "LatestVersionNumber": 0,
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ],
  "NextToken": "string"
}
```

---

### 6.4 `aws ec2 describe-launch-template-versions`

**Description:** Describes one or more versions of a launch template. Can describe all versions, specific versions, or a range. Paginated.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-template-id` | string | Optional* | Template ID |
| `--launch-template-name` | string | Optional* | Template name |
| `--versions` | list(string) | Optional | Versions: `$Latest`, `$Default`, or numbers |
| `--min-version` | string | Optional | Minimum version number |
| `--max-version` | string | Optional | Maximum version number |
| `--filters` | list(structure) | Optional | Filter criteria |
| `--resolve-alias` / `--no-resolve-alias` | boolean | Optional | Resolve SSM parameter to AMI ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

*Must specify one of `--launch-template-id` or `--launch-template-name`.

#### Output Schema

```json
{
  "LaunchTemplateVersions": [
    {
      "LaunchTemplateId": "string",
      "LaunchTemplateName": "string",
      "VersionNumber": 1,
      "VersionDescription": "string",
      "CreateTime": "timestamp",
      "CreatedBy": "string",
      "DefaultVersion": true,
      "LaunchTemplateData": {
        "ImageId": "string",
        "InstanceType": "string",
        "KeyName": "string",
        "SecurityGroupIds": ["string"],
        "SecurityGroups": ["string"],
        "UserData": "string",
        "EbsOptimized": false,
        "IamInstanceProfile": { "Arn": "string", "Name": "string" },
        "Monitoring": { "Enabled": false },
        "NetworkInterfaces": [
          {
            "DeviceIndex": 0,
            "SubnetId": "string",
            "Groups": ["string"],
            "AssociatePublicIpAddress": false,
            "PrivateIpAddress": "string",
            "DeleteOnTermination": true,
            "InterfaceType": "string"
          }
        ],
        "Placement": {
          "AvailabilityZone": "string",
          "Tenancy": "string",
          "GroupName": "string",
          "HostId": "string"
        },
        "BlockDeviceMappings": [
          {
            "DeviceName": "string",
            "Ebs": {
              "VolumeSize": 0,
              "VolumeType": "string",
              "Iops": 0,
              "Throughput": 0,
              "DeleteOnTermination": true,
              "Encrypted": false,
              "SnapshotId": "string"
            }
          }
        ],
        "TagSpecifications": [
          {
            "ResourceType": "string",
            "Tags": [{ "Key": "string", "Value": "string" }]
          }
        ],
        "CreditSpecification": { "CpuCredits": "string" },
        "CpuOptions": { "CoreCount": 0, "ThreadsPerCore": 0 },
        "MetadataOptions": {
          "State": "string",
          "HttpTokens": "string",
          "HttpPutResponseHopLimit": 0,
          "HttpEndpoint": "string"
        },
        "HibernationOptions": { "Configured": false },
        "EnclaveOptions": { "Enabled": false },
        "DisableApiTermination": false,
        "InstanceInitiatedShutdownBehavior": "string"
      }
    }
  ],
  "NextToken": "string"
}
```

---

### 6.5 `aws ec2 create-launch-template-version`

**Description:** Creates a new version of an existing launch template. Versions are numbered sequentially. Can inherit from a source version and override specific parameters. Launch templates are immutable -- modifications require new versions.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-template-id` | string | Optional* | Template ID |
| `--launch-template-name` | string | Optional* | Template name |
| `--launch-template-data` | structure | **Required** | Launch template data (same structure as create-launch-template) |
| `--source-version` | string | Optional | Version to inherit from |
| `--version-description` | string | Optional | Description (max 255 chars) |
| `--client-token` | string | Optional | Idempotency token |
| `--resolve-alias` / `--no-resolve-alias` | boolean | Optional | Resolve AMI aliases |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

*Must specify one of `--launch-template-id` or `--launch-template-name`.

#### Output Schema

```json
{
  "LaunchTemplateVersion": {
    "LaunchTemplateId": "string",
    "LaunchTemplateName": "string",
    "VersionNumber": 2,
    "VersionDescription": "string",
    "CreateTime": "timestamp",
    "CreatedBy": "string",
    "DefaultVersion": false,
    "LaunchTemplateData": { "...(same structure as describe-launch-template-versions)" }
  }
}
```

---

### 6.6 `aws ec2 modify-launch-template`

**Description:** Modifies a launch template by setting which version is the default. Does not modify the template data itself.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-template-id` | string | Optional* | Template ID |
| `--launch-template-name` | string | Optional* | Template name |
| `--default-version` | string | Optional | Version number to set as default |
| `--client-token` | string | Optional | Idempotency token |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

*Must specify one of `--launch-template-id` or `--launch-template-name`.

#### Output Schema

```json
{
  "LaunchTemplate": {
    "LaunchTemplateId": "string",
    "LaunchTemplateName": "string",
    "CreateTime": "timestamp",
    "CreatedBy": "string",
    "DefaultVersionNumber": 2,
    "LatestVersionNumber": 3,
    "Tags": [{ "Key": "string", "Value": "string" }]
  }
}
```

---

