# Certificates

### 10.1 `create-certificate`

Creates an SSL/TLS certificate for use with Lightsail distributions or container services.

**Synopsis:**
```bash
aws lightsail create-certificate \
    --certificate-name <value> \
    --domain-name <value> \
    [--subject-alternative-names <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-name` | **Yes** | string | -- | Name for the certificate |
| `--domain-name` | **Yes** | string | -- | Primary domain name |
| `--subject-alternative-names` | No | list(string) | None | Subject alternative names |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "certificate": {
        "certificateArn": "string",
        "certificateName": "string",
        "domainName": "string",
        "certificateDetail": {
            "arn": "string",
            "name": "string",
            "domainName": "string",
            "status": "PENDING_VALIDATION|ISSUED|INACTIVE|EXPIRED|VALIDATION_TIMED_OUT|REVOKED|FAILED",
            "serialNumber": "string",
            "subjectAlternativeNames": ["string"],
            "domainValidationRecords": [
                {
                    "domainName": "string",
                    "validationStatus": "PENDING_VALIDATION|FAILED|SUCCESS",
                    "resourceRecord": {
                        "name": "string",
                        "type": "string",
                        "value": "string"
                    },
                    "dnsRecordCreationState": {
                        "code": "SUCCEEDED|STARTED|FAILED",
                        "message": "string"
                    }
                }
            ],
            "requestFailureReason": "string",
            "inUseResourceCount": "integer",
            "keyAlgorithm": "string",
            "createdAt": "timestamp",
            "issuedAt": "timestamp",
            "issuerCA": "string",
            "notBefore": "timestamp",
            "notAfter": "timestamp",
            "eligibleToRenew": "string",
            "renewalSummary": {
                "domainValidationRecords": [],
                "renewalStatus": "PendingAutoRenewal|PendingValidation|Success|Failed",
                "renewalStatusReason": "string",
                "updatedAt": "timestamp"
            },
            "revokedAt": "timestamp",
            "revocationReason": "string",
            "tags": [],
            "supportCode": "string"
        },
        "tags": []
    },
    "operations": []
}
```

---

### 10.2 `delete-certificate`

Deletes an SSL/TLS certificate.

**Synopsis:**
```bash
aws lightsail delete-certificate \
    --certificate-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-name` | **Yes** | string | -- | Name of the certificate to delete |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Certificate",
            "operationType": "DeleteCertificate",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 10.3 `get-certificates`

Returns information about certificates. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-certificates \
    [--certificate-statuses <value>] \
    [--include-certificate-details | --no-include-certificate-details] \
    [--certificate-name <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-statuses` | No | list(string) | None | Filter by status: `PENDING_VALIDATION`, `ISSUED`, `INACTIVE`, `EXPIRED`, `VALIDATION_TIMED_OUT`, `REVOKED`, `FAILED` |
| `--include-certificate-details` | No | boolean | false | Include full certificate details |
| `--certificate-name` | No | string | None | Specific certificate name |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "certificates": [
        {
            "certificateArn": "string",
            "certificateName": "string",
            "domainName": "string",
            "certificateDetail": {},
            "tags": []
        }
    ],
    "nextPageToken": "string"
}
```
