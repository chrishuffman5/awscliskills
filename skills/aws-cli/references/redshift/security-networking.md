# Security & Networking

### 4.1 `create-cluster-security-group`

Creates a new Amazon Redshift cluster security group (EC2-Classic).

**Synopsis:**
```bash
aws redshift create-cluster-security-group \
    --cluster-security-group-name <value> \
    --description <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-security-group-name` | **Yes** | string | -- | Security group name |
| `--description` | **Yes** | string | -- | Description |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ClusterSecurityGroup": {
        "ClusterSecurityGroupName": "string",
        "Description": "string",
        "EC2SecurityGroups": [],
        "IPRanges": [],
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 4.2 `delete-cluster-security-group`

Deletes a cluster security group.

**Synopsis:**
```bash
aws redshift delete-cluster-security-group \
    --cluster-security-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-security-group-name` | **Yes** | string | -- | Security group to delete |

No output on success.

---

### 4.3 `describe-cluster-security-groups`

Returns cluster security group information. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-cluster-security-groups \
    [--cluster-security-group-name <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-security-group-name` | No | string | -- | Specific security group |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ClusterSecurityGroups": [
        {
            "ClusterSecurityGroupName": "string",
            "Description": "string",
            "EC2SecurityGroups": [
                {
                    "Status": "string",
                    "EC2SecurityGroupName": "string",
                    "EC2SecurityGroupOwnerId": "string",
                    "Tags": []
                }
            ],
            "IPRanges": [
                {
                    "Status": "string",
                    "CIDRIP": "string",
                    "Tags": []
                }
            ],
            "Tags": []
        }
    ],
    "Marker": "string"
}
```

---

### 4.4 `authorize-cluster-security-group-ingress`

Adds an ingress rule to a cluster security group.

**Synopsis:**
```bash
aws redshift authorize-cluster-security-group-ingress \
    --cluster-security-group-name <value> \
    [--cidrip <value>] \
    [--ec2-security-group-name <value>] \
    [--ec2-security-group-owner-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-security-group-name` | **Yes** | string | -- | Security group to modify |
| `--cidrip` | No | string | -- | CIDR IP range to authorize |
| `--ec2-security-group-name` | No | string | -- | EC2 security group name |
| `--ec2-security-group-owner-id` | No | string | -- | Owner of the EC2 security group |

**Output Schema:**
```json
{
    "ClusterSecurityGroup": {
        "ClusterSecurityGroupName": "string",
        "Description": "string",
        "EC2SecurityGroups": [],
        "IPRanges": []
    }
}
```

---

### 4.5 `revoke-cluster-security-group-ingress`

Revokes an ingress rule from a cluster security group.

**Synopsis:**
```bash
aws redshift revoke-cluster-security-group-ingress \
    --cluster-security-group-name <value> \
    [--cidrip <value>] \
    [--ec2-security-group-name <value>] \
    [--ec2-security-group-owner-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-security-group-name` | **Yes** | string | -- | Security group to modify |
| `--cidrip` | No | string | -- | CIDR IP range to revoke |
| `--ec2-security-group-name` | No | string | -- | EC2 security group name |
| `--ec2-security-group-owner-id` | No | string | -- | Owner of the EC2 security group |

**Output Schema:**
```json
{
    "ClusterSecurityGroup": {
        "ClusterSecurityGroupName": "string",
        "EC2SecurityGroups": [],
        "IPRanges": []
    }
}
```

---

### 4.6 `create-cluster-subnet-group`

Creates a new cluster subnet group.

**Synopsis:**
```bash
aws redshift create-cluster-subnet-group \
    --cluster-subnet-group-name <value> \
    --description <value> \
    --subnet-ids <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-subnet-group-name` | **Yes** | string | -- | Subnet group name |
| `--description` | **Yes** | string | -- | Description |
| `--subnet-ids` | **Yes** | list(string) | -- | List of VPC subnet IDs |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "ClusterSubnetGroup": {
        "ClusterSubnetGroupName": "string",
        "Description": "string",
        "VpcId": "string",
        "SubnetGroupStatus": "Complete|Incomplete",
        "Subnets": [
            {
                "SubnetIdentifier": "string",
                "SubnetAvailabilityZone": {
                    "Name": "string",
                    "SupportedPlatforms": [{"Name": "string"}]
                },
                "SubnetStatus": "string"
            }
        ],
        "Tags": [{"Key": "string", "Value": "string"}],
        "SupportedClusterIpAddressTypes": ["string"]
    }
}
```

---

### 4.7 `delete-cluster-subnet-group`

Deletes a cluster subnet group.

**Synopsis:**
```bash
aws redshift delete-cluster-subnet-group \
    --cluster-subnet-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-subnet-group-name` | **Yes** | string | -- | Subnet group to delete |

No output on success.

---

### 4.8 `describe-cluster-subnet-groups`

Returns subnet group descriptions. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-cluster-subnet-groups \
    [--cluster-subnet-group-name <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-subnet-group-name` | No | string | -- | Specific subnet group |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ClusterSubnetGroups": [
        {
            "ClusterSubnetGroupName": "string",
            "Description": "string",
            "VpcId": "string",
            "SubnetGroupStatus": "string",
            "Subnets": [],
            "Tags": [],
            "SupportedClusterIpAddressTypes": ["string"]
        }
    ],
    "Marker": "string"
}
```

---

### 4.9 `modify-cluster-subnet-group`

Modifies a cluster subnet group.

**Synopsis:**
```bash
aws redshift modify-cluster-subnet-group \
    --cluster-subnet-group-name <value> \
    --subnet-ids <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-subnet-group-name` | **Yes** | string | -- | Subnet group to modify |
| `--subnet-ids` | **Yes** | list(string) | -- | New list of subnet IDs |
| `--description` | No | string | -- | New description |

**Output Schema:**
```json
{
    "ClusterSubnetGroup": {
        "ClusterSubnetGroupName": "string",
        "Description": "string",
        "VpcId": "string",
        "SubnetGroupStatus": "string",
        "Subnets": [],
        "Tags": []
    }
}
```

---

### 4.10 `modify-cluster-iam-roles`

Adds or removes IAM roles associated with a cluster.

**Synopsis:**
```bash
aws redshift modify-cluster-iam-roles \
    --cluster-identifier <value> \
    [--add-iam-roles <value>] \
    [--remove-iam-roles <value>] \
    [--default-iam-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to modify |
| `--add-iam-roles` | No | list(string) | -- | IAM role ARNs to add |
| `--remove-iam-roles` | No | list(string) | -- | IAM role ARNs to remove |
| `--default-iam-role-arn` | No | string | -- | Set the default IAM role |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "IamRoles": [
            {
                "IamRoleArn": "string",
                "ApplyStatus": "in-sync|adding|removing"
            }
        ],
        "DefaultIamRoleArn": "string"
    }
}
```

---

### 4.11 `create-endpoint-access`

Creates a Redshift-managed VPC endpoint.

**Synopsis:**
```bash
aws redshift create-endpoint-access \
    --endpoint-name <value> \
    --subnet-group-name <value> \
    [--cluster-identifier <value>] \
    [--resource-owner <value>] \
    [--vpc-security-group-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--subnet-group-name` | **Yes** | string | -- | Subnet group for the endpoint |
| `--cluster-identifier` | No | string | -- | Cluster identifier |
| `--resource-owner` | No | string | -- | Account that owns the cluster |
| `--vpc-security-group-ids` | No | list(string) | -- | VPC security group IDs |

**Output Schema:**
```json
{
    "ClusterIdentifier": "string",
    "ResourceOwner": "string",
    "SubnetGroupName": "string",
    "EndpointStatus": "creating|active|deleting|modifying",
    "EndpointName": "string",
    "EndpointCreateTime": "timestamp",
    "Port": "integer",
    "Address": "string",
    "VpcSecurityGroups": [
        {
            "VpcSecurityGroupId": "string",
            "Status": "string"
        }
    ],
    "VpcEndpoint": {
        "VpcEndpointId": "string",
        "VpcId": "string",
        "NetworkInterfaces": [
            {
                "NetworkInterfaceId": "string",
                "SubnetId": "string",
                "PrivateIpAddress": "string",
                "AvailabilityZone": "string"
            }
        ]
    }
}
```

---

### 4.12 `delete-endpoint-access`

Deletes a Redshift-managed VPC endpoint.

**Synopsis:**
```bash
aws redshift delete-endpoint-access \
    --endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint to delete |

**Output Schema:**
```json
{
    "ClusterIdentifier": "string",
    "EndpointStatus": "deleting",
    "EndpointName": "string"
}
```

---

### 4.13 `describe-endpoint-access`

Describes Redshift-managed VPC endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-endpoint-access \
    [--cluster-identifier <value>] \
    [--resource-owner <value>] \
    [--endpoint-name <value>] \
    [--vpc-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | No | string | -- | Filter by cluster |
| `--resource-owner` | No | string | -- | Filter by resource owner |
| `--endpoint-name` | No | string | -- | Specific endpoint |
| `--vpc-id` | No | string | -- | Filter by VPC |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "EndpointAccessList": [
        {
            "ClusterIdentifier": "string",
            "ResourceOwner": "string",
            "SubnetGroupName": "string",
            "EndpointStatus": "string",
            "EndpointName": "string",
            "EndpointCreateTime": "timestamp",
            "Port": "integer",
            "Address": "string",
            "VpcSecurityGroups": [],
            "VpcEndpoint": {}
        }
    ],
    "Marker": "string"
}
```

---

### 4.14 `modify-endpoint-access`

Modifies a Redshift-managed VPC endpoint.

**Synopsis:**
```bash
aws redshift modify-endpoint-access \
    --endpoint-name <value> \
    [--vpc-security-group-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint to modify |
| `--vpc-security-group-ids` | No | list(string) | -- | New security group IDs |

**Output Schema:**
```json
{
    "ClusterIdentifier": "string",
    "EndpointStatus": "modifying",
    "EndpointName": "string",
    "VpcSecurityGroups": [],
    "VpcEndpoint": {}
}
```

---

### 4.15 `create-authentication-profile`

Creates an authentication profile with specified content.

**Synopsis:**
```bash
aws redshift create-authentication-profile \
    --authentication-profile-name <value> \
    --authentication-profile-content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authentication-profile-name` | **Yes** | string | -- | Profile name |
| `--authentication-profile-content` | **Yes** | string | -- | JSON content for the profile |

**Output Schema:**
```json
{
    "AuthenticationProfileName": "string",
    "AuthenticationProfileContent": "string"
}
```

---

### 4.16 `delete-authentication-profile`

Deletes an authentication profile.

**Synopsis:**
```bash
aws redshift delete-authentication-profile \
    --authentication-profile-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authentication-profile-name` | **Yes** | string | -- | Profile to delete |

**Output Schema:**
```json
{
    "AuthenticationProfileName": "string"
}
```

---

### 4.17 `describe-authentication-profiles`

Describes authentication profiles.

**Synopsis:**
```bash
aws redshift describe-authentication-profiles \
    [--authentication-profile-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authentication-profile-name` | No | string | -- | Specific profile name |

**Output Schema:**
```json
{
    "AuthenticationProfiles": [
        {
            "AuthenticationProfileName": "string",
            "AuthenticationProfileContent": "string"
        }
    ]
}
```

---

### 4.18 `modify-cluster-maintenance`

Modifies the maintenance settings of a cluster.

**Synopsis:**
```bash
aws redshift modify-cluster-maintenance \
    --cluster-identifier <value> \
    [--defer-maintenance | --no-defer-maintenance] \
    [--defer-maintenance-identifier <value>] \
    [--defer-maintenance-start-time <value>] \
    [--defer-maintenance-end-time <value>] \
    [--defer-maintenance-duration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to modify |
| `--defer-maintenance` | No | boolean | -- | Enable deferred maintenance |
| `--defer-maintenance-identifier` | No | string | -- | Identifier of deferred maintenance window |
| `--defer-maintenance-start-time` | No | timestamp | -- | Start time of deferred window |
| `--defer-maintenance-end-time` | No | timestamp | -- | End time of deferred window |
| `--defer-maintenance-duration` | No | integer | -- | Duration in days (max 45) |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "DeferredMaintenanceWindows": [
            {
                "DeferMaintenanceIdentifier": "string",
                "DeferMaintenanceStartTime": "timestamp",
                "DeferMaintenanceEndTime": "timestamp"
            }
        ]
    }
}
```
