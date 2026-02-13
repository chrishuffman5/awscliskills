# SAML Providers

### 15.1 `create-saml-provider`

Creates a SAML provider resource using an IdP metadata document.

**Synopsis:**
```bash
aws iam create-saml-provider \
    --saml-metadata-document <value> \
    --name <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--saml-metadata-document` | **Yes** | string | -- | XML metadata (1-10000000 chars). Use `file://` |
| `--name` | **Yes** | string | -- | Provider name (1-128 chars). Pattern: `[\w._-]+` |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "SAMLProviderArn": "string",
    "Tags": [{ "Key": "string", "Value": "string" }]
}
```

---

### 15.2 `get-saml-provider`

Returns the SAML provider metadata document.

**Synopsis:**
```bash
aws iam get-saml-provider --saml-provider-arn <value>
```

**Output Schema:**
```json
{
    "SAMLMetadataDocument": "string",
    "CreateDate": "timestamp",
    "ValidUntil": "timestamp",
    "Tags": [{ "Key": "string", "Value": "string" }]
}
```

---

### 15.3 `list-saml-providers`

Lists all SAML providers in the account.

**Synopsis:**
```bash
aws iam list-saml-providers
```

**Output Schema:**
```json
{
    "SAMLProviderList": [
        {
            "Arn": "string",
            "ValidUntil": "timestamp",
            "CreateDate": "timestamp"
        }
    ]
}
```

---

### 15.4 `update-saml-provider`

Updates the metadata document for an existing SAML provider.

**Synopsis:**
```bash
aws iam update-saml-provider --saml-provider-arn <value> --saml-metadata-document <value>
```

**Output Schema:**
```json
{
    "SAMLProviderArn": "string"
}
```

---

### 15.5 `delete-saml-provider`

Deletes a SAML provider.

**Synopsis:**
```bash
aws iam delete-saml-provider --saml-provider-arn <value>
```

**Output:** None on success.

---
