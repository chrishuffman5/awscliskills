# Identity, Keys & Tags

### 20.1 `describe-ip-restriction` / `update-ip-restriction`

Manage IP restrictions for QuickSight access.

**Synopsis:**
```bash
aws quicksight describe-ip-restriction \
    --aws-account-id <value>

aws quicksight update-ip-restriction \
    --aws-account-id <value> \
    [--ip-restriction-rule-map <value>] \
    [--vpc-id-restriction-rule-map <value>] \
    [--vpc-endpoint-id-restriction-rule-map <value>] \
    [--enabled | --no-enabled]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--ip-restriction-rule-map` | No | map | unchanged | CIDR to description map |
| `--vpc-id-restriction-rule-map` | No | map | unchanged | VPC ID to description map |
| `--vpc-endpoint-id-restriction-rule-map` | No | map | unchanged | VPC endpoint ID to description map |
| `--enabled` | No | boolean | unchanged | Enable/disable IP restrictions |

**Output Schema (describe):**
```json
{
    "AwsAccountId": "string",
    "IpRestrictionRuleMap": {
        "CIDR": "description"
    },
    "VpcIdRestrictionRuleMap": {},
    "VpcEndpointIdRestrictionRuleMap": {},
    "Enabled": "boolean",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 20.2 `describe-key-registration` / `update-key-registration`

Manage customer-managed key (CMK) registration for QuickSight.

**Synopsis:**
```bash
aws quicksight describe-key-registration \
    --aws-account-id <value> \
    [--default-key-only | --no-default-key-only]

aws quicksight update-key-registration \
    --aws-account-id <value> \
    --key-registration <value>
```

---

### 20.3 `list-identity-propagation-configs` / `update-identity-propagation-config` / `delete-identity-propagation-config`

Manage identity propagation from QuickSight to downstream AWS services.

**Synopsis:**
```bash
aws quicksight list-identity-propagation-configs --aws-account-id <value>

aws quicksight update-identity-propagation-config \
    --aws-account-id <value> \
    --service <value> \
    [--authorized-targets <value>]

aws quicksight delete-identity-propagation-config \
    --aws-account-id <value> \
    --service <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service` | **Yes** | string | -- | AWS service name (e.g., `REDSHIFT`) |
| `--authorized-targets` | No | list(string) | None | Authorized target ARNs |

---

### 20.4 `update-public-sharing-settings`

Updates public sharing settings (enable/disable public dashboards).

**Synopsis:**
```bash
aws quicksight update-public-sharing-settings \
    --aws-account-id <value> \
    [--public-sharing-enabled | --no-public-sharing-enabled]
```

---

### 20.5 `get-identity-context`

Returns the identity context for the calling user.

**Synopsis:**
```bash
aws quicksight get-identity-context \
    --aws-account-id <value>
```

---

### 20.6 `tag-resource` / `untag-resource` / `list-tags-for-resource`

Manage resource tags.

**Synopsis:**
```bash
aws quicksight tag-resource \
    --resource-arn <value> \
    --tags <value>

aws quicksight untag-resource \
    --resource-arn <value> \
    --tag-keys <value>

aws quicksight list-tags-for-resource \
    --resource-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the QuickSight resource |
| `--tags` | **Yes** | list | -- | Tags to add. `Key=string,Value=string ...` |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema (list-tags):**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "RequestId": "string",
    "Status": "integer"
}
```
