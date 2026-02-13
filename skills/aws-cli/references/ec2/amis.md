# AMIs

### 5.1 `aws ec2 describe-images`

**Description:** Describes AMIs available to you (public, owned, and those with explicit launch permissions). Uses eventual consistency. Pagination recommended.

**ECS-Optimized AMI Lookup Example:**
```bash
aws ec2 describe-images \
    --owners amazon \
    --filters "Name=name,Values=amzn2-ami-ecs-hvm-*-x86_64-ebs" \
    --query 'sort_by(Images, &CreationDate)[-1].[ImageId,Name]' \
    --output text
```

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--image-ids` | list(string) | Optional | Specific AMI IDs |
| `--owners` | list(string) | Optional | Owner filter: account IDs, `self`, `amazon`, `aws-marketplace` |
| `--executable-users` | list(string) | Optional | Users with launch permissions: account IDs, `self`, `all` |
| `--filters` | list(structure) | Optional | Filter criteria (see below) |
| `--include-deprecated` / `--no-include-deprecated` | boolean | Optional | Include deprecated AMIs (default: false) |
| `--include-disabled` / `--no-include-disabled` | boolean | Optional | Include disabled AMIs (default: false) |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

**Common Filters:** `architecture` (`i386`/`x86_64`/`arm64`), `state` (`available`/`pending`/`failed`), `is-public`, `owner-id`, `owner-alias`, `name`, `image-id`, `root-device-type` (`ebs`/`instance-store`), `tag:<key>`, `tag-key`, `creation-date`, `ena-support`, `hypervisor`

#### Output Schema

```json
{
  "NextToken": "string",
  "Images": [
    {
      "ImageId": "string",
      "ImageLocation": "string",
      "State": "pending|available|invalid|deregistered|failed|disabled",
      "OwnerId": "string",
      "CreationDate": "string",
      "Public": false,
      "Architecture": "i386|x86_64|arm64",
      "RootDeviceType": "ebs|instance-store",
      "RootDeviceName": "string",
      "BlockDeviceMappings": [
        {
          "DeviceName": "string",
          "Ebs": {
            "SnapshotId": "string",
            "VolumeSize": 0,
            "VolumeType": "standard|io1|io2|gp2|gp3|sc1|st1",
            "DeleteOnTermination": true,
            "Encrypted": false,
            "Iops": 0,
            "Throughput": 0
          }
        }
      ],
      "VirtualizationType": "hvm|paravirtual",
      "Hypervisor": "ovm|xen",
      "Name": "string",
      "Description": "string",
      "EnaSupport": true,
      "BootMode": "legacy-bios|uefi|uefi-preferred",
      "TpmSupport": "v2.0",
      "ImdsSupport": "v2.0",
      "PlatformDetails": "string",
      "UsageOperation": "string",
      "Tags": [{ "Key": "string", "Value": "string" }],
      "DeprecationTime": "string",
      "ImageAllowed": true,
      "FreeTierEligible": false
    }
  ]
}
```

---

