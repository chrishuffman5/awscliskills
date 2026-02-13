# Security Groups

### 2.1 `aws ec2 create-security-group`

**Description:** Creates a security group (virtual firewall) for EC2 instances. Security group names must be unique within a VPC. Cannot start with `sg-`.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--group-name` | string | **Required** | Name (max 255 chars) |
| `--description` | string | **Required** | Description (max 255 chars) |
| `--vpc-id` | string | Optional | VPC ID (required for non-default VPC) |
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "GroupId": "string",
  "Tags": [{ "Key": "string", "Value": "string" }],
  "SecurityGroupArn": "string"
}
```

---

### 2.2 `aws ec2 delete-security-group`

**Description:** Deletes a security group. Fails with `DependencyViolation` if associated with instances, network interfaces, or referenced by another group.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--group-id` | string | Optional | Security group ID |
| `--group-name` | string | Optional | Security group name (default VPC only) |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "Return": true,
  "GroupId": "string"
}
```

---

### 2.3 `aws ec2 describe-security-groups`

**Description:** Describes specified or all security groups. Paginated operation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--group-ids` | list(string) | Optional | Security group IDs |
| `--group-names` | list(string) | Optional | Security group names (default VPC only) |
| `--filters` | list(structure) | Optional | Filter criteria |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

**Filters:** `description`, `group-id`, `group-name`, `vpc-id`, `owner-id`, `tag:<key>`, `tag-key`, `ip-permission.cidr`, `ip-permission.from-port`, `ip-permission.to-port`, `ip-permission.group-id`, `ip-permission.protocol`, `egress.ip-permission.cidr`, `egress.ip-permission.from-port`, `egress.ip-permission.to-port`, `egress.ip-permission.group-id`, `egress.ip-permission.protocol`

#### Output Schema

```json
{
  "NextToken": "string",
  "SecurityGroups": [
    {
      "GroupId": "string",
      "GroupName": "string",
      "Description": "string",
      "VpcId": "string",
      "OwnerId": "string",
      "SecurityGroupArn": "string",
      "IpPermissions": [
        {
          "IpProtocol": "string",
          "FromPort": 0,
          "ToPort": 0,
          "IpRanges": [{ "CidrIp": "string", "Description": "string" }],
          "Ipv6Ranges": [{ "CidrIpv6": "string", "Description": "string" }],
          "UserIdGroupPairs": [
            {
              "GroupId": "string",
              "UserId": "string",
              "GroupName": "string",
              "VpcId": "string",
              "VpcPeeringConnectionId": "string",
              "Description": "string"
            }
          ],
          "PrefixListIds": [{ "PrefixListId": "string", "Description": "string" }]
        }
      ],
      "IpPermissionsEgress": ["(same structure as IpPermissions)"],
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ]
}
```

---

### 2.4 `aws ec2 authorize-security-group-ingress`

**Description:** Adds inbound (ingress) rules. Must specify exactly one source (CIDR, prefix list, or security group) and a protocol. For TCP/UDP, must specify port(s). For ICMP, must specify type and code.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--group-id` | string | **Required** (VPC) | Security group ID |
| `--group-name` | string | Optional | Security group name (default VPC only) |
| `--ip-permissions` | list(structure) | Optional | Complex rule definitions (recommended for multiple rules) |
| `--protocol` | string | Optional | `tcp`, `udp`, `icmp`, `icmpv6`, or `all` |
| `--port` | string | Optional | Port or range `min-max` |
| `--cidr` | string | Optional | IPv4 CIDR |
| `--source-group` | string | Optional | Source security group name or ID |
| `--group-owner` | string | Optional | AWS account ID owning source group |
| `--tag-specifications` | list(structure) | Optional | Tags for the rules |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

**IP Permissions Structure:**

```json
[
  {
    "IpProtocol": "tcp",
    "FromPort": 22,
    "ToPort": 22,
    "IpRanges": [{ "CidrIp": "0.0.0.0/0", "Description": "SSH" }],
    "Ipv6Ranges": [{ "CidrIpv6": "::/0", "Description": "SSH IPv6" }],
    "UserIdGroupPairs": [{ "GroupId": "sg-xxx", "Description": "From other SG" }],
    "PrefixListIds": [{ "PrefixListId": "pl-xxx" }]
  }
]
```

#### Output Schema

```json
{
  "Return": true,
  "SecurityGroupRules": [
    {
      "SecurityGroupRuleId": "string",
      "GroupId": "string",
      "GroupOwnerId": "string",
      "IsEgress": false,
      "IpProtocol": "string",
      "FromPort": 0,
      "ToPort": 0,
      "CidrIpv4": "string",
      "CidrIpv6": "string",
      "PrefixListId": "string",
      "ReferencedGroupInfo": {
        "GroupId": "string",
        "UserId": "string",
        "VpcId": "string"
      },
      "Description": "string",
      "Tags": [{ "Key": "string", "Value": "string" }],
      "SecurityGroupRuleArn": "string"
    }
  ]
}
```

---

### 2.5 `aws ec2 authorize-security-group-egress`

**Description:** Adds outbound (egress) rules to a VPC security group. Same structure and logic as ingress rules.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--group-id` | string | **Required** | Security group ID |
| `--ip-permissions` | list(structure) | Optional | Complex rule definitions |
| `--protocol` | string | Optional | `tcp`, `udp`, `icmp`, or `all` |
| `--port` | string | Optional | Port or range `min-max` |
| `--cidr` | string | Optional | IPv4 CIDR |
| `--source-group` | string | Optional | Destination security group |
| `--group-owner` | string | Optional | AWS account ID |
| `--tag-specifications` | list(structure) | Optional | Tags for the rules |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "Return": true,
  "SecurityGroupRules": [
    {
      "SecurityGroupRuleId": "string",
      "GroupId": "string",
      "GroupOwnerId": "string",
      "IsEgress": true,
      "IpProtocol": "string",
      "FromPort": 0,
      "ToPort": 0,
      "CidrIpv4": "string",
      "CidrIpv6": "string",
      "PrefixListId": "string",
      "ReferencedGroupInfo": { "GroupId": "string", "UserId": "string", "VpcId": "string" },
      "Description": "string",
      "Tags": [{ "Key": "string", "Value": "string" }],
      "SecurityGroupRuleArn": "string"
    }
  ]
}
```

---

### 2.6 `aws ec2 revoke-security-group-ingress`

**Description:** Removes inbound rules from a security group. Values must match existing rules exactly. In default VPCs, unmatched values silently succeed; in non-default VPCs, returns `InvalidPermission.NotFound`.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--group-id` | string | Required* | Security group ID |
| `--group-name` | string | Required* | Security group name (default VPC only) |
| `--ip-permissions` | list(structure) | Optional | Rules to revoke |
| `--security-group-rule-ids` | list(string) | Optional | Rule IDs to revoke |
| `--protocol` | string | Optional | Protocol shorthand |
| `--port` | string | Optional | Port or range |
| `--cidr` | string | Optional | IPv4 CIDR |
| `--source-group` | string | Optional | Source security group |
| `--group-owner` | string | Optional | AWS account ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

*Must specify at least one of `--group-id` or `--group-name`.

#### Output Schema

```json
{
  "Return": true,
  "UnknownIpPermissions": [
    {
      "IpProtocol": "string",
      "FromPort": 0,
      "ToPort": 0,
      "IpRanges": [{ "CidrIp": "string" }],
      "Ipv6Ranges": [{ "CidrIpv6": "string" }],
      "UserIdGroupPairs": [{ "GroupId": "string" }],
      "PrefixListIds": [{ "PrefixListId": "string" }]
    }
  ],
  "RevokedSecurityGroupRules": [
    {
      "SecurityGroupRuleId": "string",
      "GroupId": "string",
      "IsEgress": false,
      "IpProtocol": "string",
      "FromPort": 0,
      "ToPort": 0,
      "CidrIpv4": "string",
      "CidrIpv6": "string",
      "PrefixListId": "string",
      "ReferencedGroupId": "string",
      "Description": "string"
    }
  ]
}
```

---

### 2.7 `aws ec2 revoke-security-group-egress`

**Description:** Removes outbound (egress) rules from a VPC security group. Same matching requirements as ingress revocation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--group-id` | string | **Required** | Security group ID |
| `--ip-permissions` | list(structure) | Optional | Rules to revoke |
| `--security-group-rule-ids` | list(string) | Optional | Rule IDs to revoke |
| `--protocol` | string | Optional | Protocol shorthand |
| `--port` | string | Optional | Port or range |
| `--cidr` | string | Optional | IPv4 CIDR |
| `--source-group` | string | Optional | Destination security group |
| `--group-owner` | string | Optional | AWS account ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "Return": true,
  "UnknownIpPermissions": ["(same structure as ingress)"],
  "RevokedSecurityGroupRules": ["(same structure as ingress)"]
}
```

---

