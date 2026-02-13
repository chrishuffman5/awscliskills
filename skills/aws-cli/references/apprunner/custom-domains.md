# Custom Domains

### 6.1 `associate-custom-domain`

Associates a custom domain with an App Runner service.

**Synopsis:**
```bash
aws apprunner associate-custom-domain \
    --service-arn <value> \
    --domain-name <value> \
    [--enable-www-subdomain | --no-enable-www-subdomain] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the App Runner service |
| `--domain-name` | **Yes** | string | -- | Custom domain name (e.g., `example.com`) |
| `--enable-www-subdomain` | No | boolean | true | Also associate `www.` subdomain |

**Output Schema:**
```json
{
    "DNSTarget": "string",
    "ServiceArn": "string",
    "CustomDomain": {
        "DomainName": "string",
        "EnableWWWSubdomain": true|false,
        "CertificateValidationRecords": [
            {
                "Name": "string",
                "Type": "string",
                "Value": "string",
                "Status": "PENDING_VALIDATION|SUCCESS|FAILED"
            }
        ],
        "Status": "CREATING|CREATE_FAILED|ACTIVE|DELETING|DELETE_FAILED|PENDING_CERTIFICATE_DNS_VALIDATION|BINDING_CERTIFICATE"
    },
    "VpcDNSTargets": [
        {
            "VpcIngressConnectionArn": "string",
            "VpcId": "string",
            "DomainName": "string"
        }
    ]
}
```

---

### 6.2 `disassociate-custom-domain`

Disassociates a custom domain from an App Runner service.

**Synopsis:**
```bash
aws apprunner disassociate-custom-domain \
    --service-arn <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the App Runner service |
| `--domain-name` | **Yes** | string | -- | Custom domain name to disassociate |

**Output Schema:**
```json
{
    "DNSTarget": "string",
    "ServiceArn": "string",
    "CustomDomain": {
        "DomainName": "string",
        "EnableWWWSubdomain": true|false,
        "Status": "DELETING"
    },
    "VpcDNSTargets": [
        {
            "VpcIngressConnectionArn": "string",
            "VpcId": "string",
            "DomainName": "string"
        }
    ]
}
```

---

### 6.3 `describe-custom-domains`

Returns descriptions of custom domains associated with an App Runner service. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner describe-custom-domains \
    --service-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the App Runner service |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DNSTarget": "string",
    "ServiceArn": "string",
    "CustomDomains": [
        {
            "DomainName": "string",
            "EnableWWWSubdomain": true|false,
            "CertificateValidationRecords": [
                {
                    "Name": "string",
                    "Type": "string",
                    "Value": "string",
                    "Status": "PENDING_VALIDATION|SUCCESS|FAILED"
                }
            ],
            "Status": "CREATING|CREATE_FAILED|ACTIVE|DELETING|DELETE_FAILED|PENDING_CERTIFICATE_DNS_VALIDATION|BINDING_CERTIFICATE"
        }
    ],
    "VpcDNSTargets": [
        {
            "VpcIngressConnectionArn": "string",
            "VpcId": "string",
            "DomainName": "string"
        }
    ],
    "NextToken": "string"
}
```
