# Instances

### 1.1 `aws ec2 run-instances`

**Description:** Launches the specified number of instances using an AMI. Allows extensive customization of instance configuration, networking, storage, and security options. If no subnet is specified, a default subnet from the default VPC is used. All instances get a primary private IPv4 address. Break large requests into smaller batches for faster launches.

#### Parameters

**Required:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--image-id` | string | AMI ID to launch |
| `--instance-type` | string | Instance type (e.g., `t2.micro`, `m5.large`, `c5.xlarge`) |

**Network & Connectivity (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--subnet-id` | string | VPC subnet ID |
| `--security-group-ids` | list(string) | Security group IDs (VPC) |
| `--security-groups` | list(string) | Security group names (default VPC) |
| `--private-ip-address` | string | Primary IPv4 address from subnet range |
| `--network-interfaces` | list(structure) | Network interfaces to attach. Fields: `DeviceIndex` (int), `SubnetId` (string), `Groups` (list), `PrivateIpAddress` (string), `AssociatePublicIpAddress` (bool), `Ipv6AddressCount` (int), `Ipv6Addresses` (list), `InterfaceType` (string: `interface`/`efa`/`efa-only`) |
| `--ipv6-address-count` | integer | Number of IPv6 addresses |
| `--ipv6-addresses` | list(structure) | Specific IPv6 addresses |
| `--associate-public-ip-address` / `--no-associate-public-ip-address` | boolean | Associate public IP |
| `--enable-primary-ipv6` / `--no-enable-primary-ipv6` | boolean | Enable primary IPv6 GUA |

**Storage & Volumes (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--block-device-mappings` | list(structure) | EBS and instance store volumes. Fields: `DeviceName` (string), `Ebs` (structure: `VolumeSize` int GiB, `VolumeType` string [`standard`/`io1`/`io2`/`gp2`/`gp3`/`sc1`/`st1`], `Iops` int, `Throughput` int MiB/s gp3 only, `DeleteOnTermination` bool, `Encrypted` bool, `KmsKeyId` string, `SnapshotId` string), `VirtualName` (string), `NoDevice` (string) |
| `--ebs-optimized` / `--no-ebs-optimized` | boolean | Optimize for EBS I/O |

**Key Pair & Access (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--key-name` | string | EC2 key pair name |

**Instance Configuration (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--count` | string | Number of instances or range `min:max` |
| `--user-data` | string | Base64-encoded user data script |
| `--instance-initiated-shutdown-behavior` | string | `stop` or `terminate` |
| `--monitoring` | structure | `{Enabled: bool}` - detailed monitoring |
| `--cpu-options` | structure | `{CoreCount: int, ThreadsPerCore: int, AmdSevSnp: string}` |

**Placement & Tenancy (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--placement` | structure | `{AvailabilityZone, GroupName, GroupId, Tenancy [default/dedicated/host], Affinity, HostId, PartitionNumber, HostResourceGroupArn}` |

**Launch Template (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--launch-template` | structure | `{LaunchTemplateId, LaunchTemplateName, Version}` - Version can be `$Latest`, `$Default`, or number |

**Purchasing Options (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--instance-market-options` | structure | `{MarketType: [spot/capacity-block], SpotOptions: {MaxPrice, SpotInstanceType [one-time/persistent], InstanceInterruptionBehavior [hibernate/stop/terminate], ValidUntil}}` |

**Performance (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--credit-specification` | structure | `{CpuCredits: [standard/unlimited]}` for T instances |
| `--network-performance-options` | structure | `{BandwidthWeighting: [default/vpc-1/ebs-1]}` |

**IAM (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--iam-instance-profile` | structure | `{Arn: string}` or `{Name: string}` |

**Metadata (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--metadata-options` | structure | `{HttpTokens: [optional/required], HttpPutResponseHopLimit: int 1-64, HttpEndpoint: [enabled/disabled], HttpProtocolIpv6: [enabled/disabled], InstanceMetadataTags: [enabled/disabled]}` |
| `--private-dns-name-options` | structure | `{HostnameType: [ip-name/resource-name], EnableResourceNameDnsARecord: bool, EnableResourceNameDnsAAAARecord: bool}` |

**Security & Protection (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--disable-api-termination` / `--enable-api-termination` | boolean | Termination protection |
| `--disable-api-stop` / `--no-disable-api-stop` | boolean | Stop protection |

**Advanced (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--hibernation-options` | structure | `{Configured: bool}` |
| `--enclave-options` | structure | `{Enabled: bool}` - Nitro Enclaves |
| `--capacity-reservation-specification` | structure | `{CapacityReservationPreference: [capacity-reservations-only/open/none], CapacityReservationTarget: {CapacityReservationId, CapacityReservationResourceGroupArn}}` |
| `--license-specifications` | list(structure) | `{LicenseConfigurationArn: string}` |
| `--maintenance-options` | structure | `{AutoRecovery: [disabled/default]}` |

**Tagging (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--tag-specifications` | list(structure) | `{ResourceType: [instance/volume/network-interface/...], Tags: [{Key, Value}]}` |

**Other (Optional):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--client-token` | string | Idempotency token (max 64 ASCII chars) |
| `--dry-run` / `--no-dry-run` | boolean | Test without making changes |

#### Output Schema

The output is extensive. Key top-level fields in the response:

```json
{
  "Instances": [
    {
      "InstanceId": "string",
      "ImageId": "string",
      "InstanceType": "string",
      "State": { "Code": 0, "Name": "pending" },
      "PrivateDnsName": "string",
      "PublicDnsName": "string",
      "PrivateIpAddress": "string",
      "PublicIpAddress": "string",
      "KeyName": "string",
      "VpcId": "string",
      "SubnetId": "string",
      "LaunchTime": "timestamp",
      "Placement": {
        "AvailabilityZone": "string",
        "Tenancy": "string"
      },
      "SecurityGroups": [{ "GroupId": "string", "GroupName": "string" }],
      "NetworkInterfaces": [
        {
          "NetworkInterfaceId": "string",
          "SubnetId": "string",
          "VpcId": "string",
          "PrivateIpAddress": "string",
          "Association": { "PublicIp": "string" },
          "Groups": [{ "GroupId": "string", "GroupName": "string" }],
          "Attachment": { "AttachmentId": "string", "DeviceIndex": 0 }
        }
      ],
      "BlockDeviceMappings": [
        {
          "DeviceName": "string",
          "Ebs": {
            "VolumeId": "string",
            "Status": "string",
            "DeleteOnTermination": true
          }
        }
      ],
      "IamInstanceProfile": { "Arn": "string", "Id": "string" },
      "Tags": [{ "Key": "string", "Value": "string" }],
      "Architecture": "string",
      "EbsOptimized": false,
      "Monitoring": { "State": "string" },
      "MetadataOptions": {
        "State": "string",
        "HttpTokens": "string",
        "HttpPutResponseHopLimit": 1,
        "HttpEndpoint": "string"
      }
    }
  ],
  "OwnerId": "string",
  "ReservationId": "string"
}
```

---

### 1.2 `aws ec2 describe-instances`

**Description:** Describes specified or all EC2 instances. Returns instance configuration, state, networking, block devices, security groups, and tags. Uses eventual consistency model. Pagination recommended.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--instance-ids` | list(string) | Optional | Specific instance IDs |
| `--filters` | list(structure) | Optional | Filter criteria (see below) |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

**Common Filters:**
- `instance-id`, `instance-state-name` (`pending`/`running`/`shutting-down`/`terminated`/`stopping`/`stopped`), `instance-type`, `availability-zone`, `vpc-id`, `subnet-id`, `image-id`, `key-name`, `tag:<key>`, `tag-key`, `private-ip-address`, `public-ip-address`, `security-group-id`, `security-group-name`, `architecture`, `platform`, `ebs-optimized`, `monitoring-state`

#### Output Schema

```json
{
  "NextToken": "string",
  "Reservations": [
    {
      "ReservationId": "string",
      "OwnerId": "string",
      "Groups": [{ "GroupId": "string", "GroupName": "string" }],
      "Instances": [
        {
          "InstanceId": "string",
          "ImageId": "string",
          "State": { "Code": 16, "Name": "running" },
          "PrivateDnsName": "string",
          "PublicDnsName": "string",
          "PrivateIpAddress": "string",
          "PublicIpAddress": "string",
          "InstanceType": "string",
          "LaunchTime": "timestamp",
          "Placement": {
            "AvailabilityZone": "string",
            "GroupName": "string",
            "Tenancy": "string",
            "PartitionNumber": 0
          },
          "KeyName": "string",
          "VpcId": "string",
          "SubnetId": "string",
          "Architecture": "string",
          "RootDeviceName": "string",
          "RootDeviceType": "string",
          "SecurityGroups": [{ "GroupId": "string", "GroupName": "string" }],
          "NetworkInterfaces": [
            {
              "NetworkInterfaceId": "string",
              "SubnetId": "string",
              "VpcId": "string",
              "PrivateIpAddress": "string",
              "PrivateDnsName": "string",
              "SourceDestCheck": true,
              "Groups": [{ "GroupId": "string", "GroupName": "string" }],
              "Attachment": {
                "AttachmentId": "string",
                "DeviceIndex": 0,
                "Status": "string",
                "AttachTime": "timestamp",
                "DeleteOnTermination": true
              },
              "Association": {
                "PublicIp": "string",
                "PublicDnsName": "string",
                "IpOwnerId": "string"
              },
              "PrivateIpAddresses": [
                {
                  "PrivateIpAddress": "string",
                  "Primary": true,
                  "Association": { "PublicIp": "string" }
                }
              ],
              "Ipv6Addresses": [{ "Ipv6Address": "string", "IsPrimaryIpv6": false }]
            }
          ],
          "BlockDeviceMappings": [
            {
              "DeviceName": "string",
              "Ebs": {
                "VolumeId": "string",
                "Status": "string",
                "AttachTime": "timestamp",
                "DeleteOnTermination": true
              }
            }
          ],
          "EbsOptimized": false,
          "EnaSupport": true,
          "IamInstanceProfile": { "Arn": "string", "Id": "string" },
          "Monitoring": { "State": "string" },
          "Tags": [{ "Key": "string", "Value": "string" }],
          "CpuOptions": { "CoreCount": 1, "ThreadsPerCore": 1 },
          "MetadataOptions": {
            "State": "string",
            "HttpTokens": "string",
            "HttpPutResponseHopLimit": 1,
            "HttpEndpoint": "string",
            "HttpProtocolIpv6": "string",
            "InstanceMetadataTags": "string"
          },
          "HibernationOptions": { "Configured": false },
          "BootMode": "string",
          "PlatformDetails": "string",
          "VirtualizationType": "string",
          "SourceDestCheck": true,
          "StateReason": { "Code": "string", "Message": "string" }
        }
      ]
    }
  ]
}
```

---

### 1.3 `aws ec2 terminate-instances`

**Description:** Terminates (permanently deletes) specified EC2 instances. Idempotent and irreversible. All EBS volumes with `DeleteOnTermination=true` are deleted. Terminated instances remain visible for approximately one hour.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--instance-ids` | list(string) | **Required** | Instance IDs to terminate (up to 1000) |
| `--force` / `--no-force` | boolean | Optional | Force shutdown without flushing caches |
| `--skip-os-shutdown` / `--no-skip-os-shutdown` | boolean | Optional | Bypass graceful OS shutdown |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "TerminatingInstances": [
    {
      "InstanceId": "string",
      "CurrentState": { "Code": 32, "Name": "shutting-down" },
      "PreviousState": { "Code": 16, "Name": "running" }
    }
  ]
}
```

**State Codes:** `0`=pending, `16`=running, `32`=shutting-down, `48`=terminated, `64`=stopping, `80`=stopped

---

### 1.4 `aws ec2 start-instances`

**Description:** Starts one or more previously stopped EBS-backed instances. Stopped instances are not billed for compute but EBS volumes continue to be charged. A one-minute minimum charge applies per start. Cannot start instance-store backed instances.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--instance-ids` | list(string) | **Required** | Instance IDs to start |
| `--additional-info` | string | Optional | Reserved |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "StartingInstances": [
    {
      "InstanceId": "string",
      "CurrentState": { "Code": 0, "Name": "pending" },
      "PreviousState": { "Code": 80, "Name": "stopped" }
    }
  ]
}
```

---

### 1.5 `aws ec2 stop-instances`

**Description:** Stops an EBS-backed instance. Performs graceful OS shutdown by default. Stopped instances retain root and data volumes. Supports hibernation if enabled at launch. Can force-stop instances stuck in "stopping" state.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--instance-ids` | list(string) | **Required** | Instance IDs to stop |
| `--hibernate` / `--no-hibernate` | boolean | Optional | Hibernate instead of stop (preserves RAM) |
| `--skip-os-shutdown` / `--no-skip-os-shutdown` | boolean | Optional | Bypass graceful OS shutdown |
| `--force` / `--no-force` | boolean | Optional | Force stop if graceful shutdown times out |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "StoppingInstances": [
    {
      "InstanceId": "string",
      "CurrentState": { "Code": 64, "Name": "stopping" },
      "PreviousState": { "Code": 16, "Name": "running" }
    }
  ]
}
```

---

### 1.6 `aws ec2 reboot-instances`

**Description:** Requests a reboot of specified instances. Asynchronous operation -- only queues the reboot. If an instance does not cleanly shut down within a few minutes, EC2 performs a hard reboot.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--instance-ids` | list(string) | **Required** | Instance IDs to reboot |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

