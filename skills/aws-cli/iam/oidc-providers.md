# OIDC Providers

### 14.1 `create-open-id-connect-provider`

Creates an IAM entity to represent an OpenID Connect (OIDC) identity provider.

**Synopsis:**
```bash
aws iam create-open-id-connect-provider \
    --url <value> \
    [--client-id-list <value>] \
    [--thumbprint-list <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--url` | **Yes** | string | -- | OIDC provider URL (must begin with `https://`). 1-255 chars |
| `--client-id-list` | No | list(string) | None | Client IDs (audiences). Max 100 items, each 1-255 chars |
| `--thumbprint-list` | No | list(string) | None | Server cert thumbprints. Max 5 items, each 40-char hex SHA-1 |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "OpenIDConnectProviderArn": "string",
    "Tags": [{ "Key": "string", "Value": "string" }]
}
```

---

### 14.2 `get-open-id-connect-provider`

Returns information about an OIDC provider.

**Synopsis:**
```bash
aws iam get-open-id-connect-provider --open-id-connect-provider-arn <value>
```

**Output Schema:**
```json
{
    "Url": "string",
    "ClientIDList": ["string"],
    "ThumbprintList": ["string"],
    "CreateDate": "timestamp",
    "Tags": [{ "Key": "string", "Value": "string" }]
}
```

---

### 14.3 `list-open-id-connect-providers`

Lists all OIDC providers in the account.

**Synopsis:**
```bash
aws iam list-open-id-connect-providers
```

**Output Schema:**
```json
{
    "OpenIDConnectProviderList": [
        { "Arn": "string" }
    ]
}
```

---

### 14.4 `add-client-id-to-open-id-connect-provider`

Adds a client ID (audience) to an existing OIDC provider.

**Synopsis:**
```bash
aws iam add-client-id-to-open-id-connect-provider \
    --open-id-connect-provider-arn <value> \
    --client-id <value>
```

**Output:** None on success.

---

### 14.5 `remove-client-id-from-open-id-connect-provider`

Removes a client ID from an OIDC provider.

**Synopsis:**
```bash
aws iam remove-client-id-from-open-id-connect-provider \
    --open-id-connect-provider-arn <value> \
    --client-id <value>
```

**Output:** None on success.

---

### 14.6 `update-open-id-connect-provider-thumbprint`

Replaces the entire list of server certificate thumbprints for an OIDC provider.

**Synopsis:**
```bash
aws iam update-open-id-connect-provider-thumbprint \
    --open-id-connect-provider-arn <value> \
    --thumbprint-list <value>
```

**Output:** None on success.

---

### 14.7 `delete-open-id-connect-provider`

Deletes an OIDC identity provider. Does not update roles that reference the provider.

**Synopsis:**
```bash
aws iam delete-open-id-connect-provider --open-id-connect-provider-arn <value>
```

**Output:** None on success.

---
