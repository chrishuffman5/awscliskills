# Domains

### 3.1 `create-domain-association`

Creates a new domain association for an Amplify app.

**Synopsis:**
```bash
aws amplify create-domain-association \
    --app-id <value> \
    --domain-name <value> \
    --sub-domain-settings <value> \
    [--enable-auto-sub-domain | --no-enable-auto-sub-domain] \
    [--auto-sub-domain-creation-patterns <value>] \
    [--auto-sub-domain-iam-role <value>] \
    [--certificate-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--domain-name` | **Yes** | string | -- | Domain name (e.g., `example.com`) |
| `--sub-domain-settings` | **Yes** | list | -- | Sub-domain settings. Shorthand: `prefix=string,branchName=string ...` |
| `--enable-auto-sub-domain` | No | boolean | false | Enable auto sub-domain creation |
| `--auto-sub-domain-creation-patterns` | No | list(string) | None | Glob patterns for auto sub-domain creation |
| `--auto-sub-domain-iam-role` | No | string | None | IAM role ARN for auto sub-domain creation |
| `--certificate-settings` | No | structure | None | SSL certificate settings. Shorthand: `type=AMPLIFY_MANAGED\|CUSTOM,customCertificateArn=string` |

**Output Schema:**
```json
{
    "domainAssociation": {
        "domainAssociationArn": "string",
        "domainName": "string",
        "enableAutoSubDomain": "boolean",
        "autoSubDomainCreationPatterns": ["string"],
        "autoSubDomainIAMRole": "string",
        "domainStatus": "PENDING_VERIFICATION|IN_PROGRESS|AVAILABLE|PENDING_DEPLOYMENT|FAILED|CREATING|REQUESTING_CERTIFICATE|UPDATING",
        "statusReason": "string",
        "certificateVerificationDNSRecord": "string",
        "subDomains": [
            {
                "subDomainSetting": {
                    "prefix": "string",
                    "branchName": "string"
                },
                "verified": "boolean",
                "dnsRecord": "string"
            }
        ],
        "certificate": {
            "type": "AMPLIFY_MANAGED|CUSTOM",
            "customCertificateArn": "string",
            "certificateVerificationDNSRecord": "string"
        }
    }
}
```

---

### 3.2 `delete-domain-association`

Deletes a domain association for an Amplify app.

**Synopsis:**
```bash
aws amplify delete-domain-association \
    --app-id <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--domain-name` | **Yes** | string | -- | Domain name to delete |

**Output Schema:**
```json
{
    "domainAssociation": {
        "domainAssociationArn": "string",
        "domainName": "string",
        "enableAutoSubDomain": "boolean",
        "domainStatus": "string",
        "statusReason": "string",
        "subDomains": []
    }
}
```

---

### 3.3 `get-domain-association`

Returns the domain association for an Amplify app.

**Synopsis:**
```bash
aws amplify get-domain-association \
    --app-id <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--domain-name` | **Yes** | string | -- | Domain name |

**Output Schema:**
```json
{
    "domainAssociation": {
        "domainAssociationArn": "string",
        "domainName": "string",
        "enableAutoSubDomain": "boolean",
        "autoSubDomainCreationPatterns": ["string"],
        "autoSubDomainIAMRole": "string",
        "domainStatus": "PENDING_VERIFICATION|IN_PROGRESS|AVAILABLE|PENDING_DEPLOYMENT|FAILED|CREATING|REQUESTING_CERTIFICATE|UPDATING",
        "statusReason": "string",
        "certificateVerificationDNSRecord": "string",
        "subDomains": [
            {
                "subDomainSetting": {
                    "prefix": "string",
                    "branchName": "string"
                },
                "verified": "boolean",
                "dnsRecord": "string"
            }
        ],
        "certificate": {
            "type": "AMPLIFY_MANAGED|CUSTOM",
            "customCertificateArn": "string",
            "certificateVerificationDNSRecord": "string"
        }
    }
}
```

---

### 3.4 `list-domain-associations`

Returns the domain associations for an Amplify app. **Paginated operation.**

**Synopsis:**
```bash
aws amplify list-domain-associations \
    --app-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "domainAssociations": [
        {
            "domainAssociationArn": "string",
            "domainName": "string",
            "enableAutoSubDomain": "boolean",
            "autoSubDomainCreationPatterns": ["string"],
            "autoSubDomainIAMRole": "string",
            "domainStatus": "string",
            "statusReason": "string",
            "subDomains": [
                {
                    "subDomainSetting": {
                        "prefix": "string",
                        "branchName": "string"
                    },
                    "verified": "boolean",
                    "dnsRecord": "string"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `update-domain-association`

Updates a domain association for an Amplify app.

**Synopsis:**
```bash
aws amplify update-domain-association \
    --app-id <value> \
    --domain-name <value> \
    [--sub-domain-settings <value>] \
    [--enable-auto-sub-domain | --no-enable-auto-sub-domain] \
    [--auto-sub-domain-creation-patterns <value>] \
    [--auto-sub-domain-iam-role <value>] \
    [--certificate-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--domain-name` | **Yes** | string | -- | Domain name to update |
| `--sub-domain-settings` | No | list | None | Updated sub-domain settings. Shorthand: `prefix=string,branchName=string ...` |
| `--enable-auto-sub-domain` | No | boolean | None | Enable/disable auto sub-domain creation |
| `--auto-sub-domain-creation-patterns` | No | list(string) | None | Updated glob patterns for auto sub-domain |
| `--auto-sub-domain-iam-role` | No | string | None | Updated IAM role ARN |
| `--certificate-settings` | No | structure | None | Updated SSL certificate settings |

**Output Schema:**
```json
{
    "domainAssociation": {
        "domainAssociationArn": "string",
        "domainName": "string",
        "enableAutoSubDomain": "boolean",
        "autoSubDomainCreationPatterns": ["string"],
        "autoSubDomainIAMRole": "string",
        "domainStatus": "PENDING_VERIFICATION|IN_PROGRESS|AVAILABLE|PENDING_DEPLOYMENT|FAILED|CREATING|REQUESTING_CERTIFICATE|UPDATING",
        "statusReason": "string",
        "certificateVerificationDNSRecord": "string",
        "subDomains": [
            {
                "subDomainSetting": {
                    "prefix": "string",
                    "branchName": "string"
                },
                "verified": "boolean",
                "dnsRecord": "string"
            }
        ],
        "certificate": {
            "type": "AMPLIFY_MANAGED|CUSTOM",
            "customCertificateArn": "string",
            "certificateVerificationDNSRecord": "string"
        }
    }
}
```
