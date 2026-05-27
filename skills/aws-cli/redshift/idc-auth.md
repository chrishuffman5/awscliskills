# IDC Authentication (Identity Center)

### 9.1 `create-redshift-idc-application`

Creates an IAM Identity Center application for Redshift authentication.

**Synopsis:**
```bash
aws redshift create-redshift-idc-application \
    --idc-instance-arn <value> \
    --redshift-idc-application-name <value> \
    --idc-display-name <value> \
    --iam-role-arn <value> \
    [--identity-namespace <value>] \
    [--authorized-token-issuer-list <value>] \
    [--service-integrations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--idc-instance-arn` | **Yes** | string | -- | IAM Identity Center instance ARN |
| `--redshift-idc-application-name` | **Yes** | string | -- | Application name |
| `--idc-display-name` | **Yes** | string | -- | Display name in Identity Center |
| `--iam-role-arn` | **Yes** | string | -- | IAM role ARN for the application |
| `--identity-namespace` | No | string | -- | Identity namespace |
| `--authorized-token-issuer-list` | No | list | -- | Authorized token issuers |
| `--service-integrations` | No | list | -- | Service integrations configuration |

**Output Schema:**
```json
{
    "RedshiftIdcApplication": {
        "IdcInstanceArn": "string",
        "RedshiftIdcApplicationName": "string",
        "RedshiftIdcApplicationArn": "string",
        "IdentityNamespace": "string",
        "IdcDisplayName": "string",
        "IamRoleArn": "string",
        "IdcManagedApplicationArn": "string",
        "IdcOnboardStatus": "string",
        "AuthorizedTokenIssuerList": [
            {
                "TrustedTokenIssuerArn": "string",
                "AuthorizedAudiencesList": ["string"]
            }
        ],
        "ServiceIntegrations": [
            {
                "LakeFormation": [
                    {
                        "LakeFormationQuery": {
                            "Authorization": "Enabled|Disabled"
                        }
                    }
                ]
            }
        ]
    }
}
```

---

### 9.2 `delete-redshift-idc-application`

Deletes an IAM Identity Center application for Redshift.

**Synopsis:**
```bash
aws redshift delete-redshift-idc-application \
    --redshift-idc-application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--redshift-idc-application-arn` | **Yes** | string | -- | Application ARN to delete |

No output on success.

---

### 9.3 `describe-redshift-idc-applications`

Describes IAM Identity Center applications. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-redshift-idc-applications \
    [--redshift-idc-application-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--redshift-idc-application-arn` | No | string | -- | Specific application ARN |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "RedshiftIdcApplications": [
        {
            "IdcInstanceArn": "string",
            "RedshiftIdcApplicationName": "string",
            "RedshiftIdcApplicationArn": "string",
            "IdentityNamespace": "string",
            "IdcDisplayName": "string",
            "IamRoleArn": "string",
            "IdcManagedApplicationArn": "string",
            "IdcOnboardStatus": "string",
            "AuthorizedTokenIssuerList": [],
            "ServiceIntegrations": []
        }
    ],
    "Marker": "string"
}
```

---

### 9.4 `modify-redshift-idc-application`

Modifies an IAM Identity Center application for Redshift.

**Synopsis:**
```bash
aws redshift modify-redshift-idc-application \
    --redshift-idc-application-arn <value> \
    [--identity-namespace <value>] \
    [--iam-role-arn <value>] \
    [--idc-display-name <value>] \
    [--authorized-token-issuer-list <value>] \
    [--service-integrations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--redshift-idc-application-arn` | **Yes** | string | -- | Application ARN to modify |
| `--identity-namespace` | No | string | -- | New identity namespace |
| `--iam-role-arn` | No | string | -- | New IAM role ARN |
| `--idc-display-name` | No | string | -- | New display name |
| `--authorized-token-issuer-list` | No | list | -- | Updated token issuer list |
| `--service-integrations` | No | list | -- | Updated service integrations |

**Output Schema:**
```json
{
    "RedshiftIdcApplication": {
        "IdcInstanceArn": "string",
        "RedshiftIdcApplicationName": "string",
        "RedshiftIdcApplicationArn": "string",
        "IdentityNamespace": "string",
        "IdcDisplayName": "string",
        "IamRoleArn": "string",
        "AuthorizedTokenIssuerList": [],
        "ServiceIntegrations": []
    }
}
```
