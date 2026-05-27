# Profiles

Commands for managing AS2 profiles in Transfer Family. Profiles define AS2 identities (local or partner) for B2B transfers.

### 6.1 `create-profile`

Creates an AS2 profile (local or partner).

**Synopsis:**
```bash
aws transfer create-profile \
    --as2-id <value> \
    --profile-type <value> \
    [--certificate-ids <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--as2-id` | **Yes** | string | -- | AS2 identifier (1-128 chars, no spaces) |
| `--profile-type` | **Yes** | string | -- | `LOCAL` or `PARTNER` |
| `--certificate-ids` | No | list(string) | None | Certificate IDs for the profile |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "ProfileId": "string"
}
```

---

### 6.2 `delete-profile`

Deletes a profile.

**Synopsis:**
```bash
aws transfer delete-profile \
    --profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | Profile ID |

**Output:** None on success.

---

### 6.3 `describe-profile`

Gets details about a profile.

**Synopsis:**
```bash
aws transfer describe-profile \
    --profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | Profile ID |

**Output Schema:**
```json
{
    "Profile": {
        "Arn": "string",
        "ProfileId": "string",
        "ProfileType": "LOCAL|PARTNER",
        "As2Id": "string",
        "CertificateIds": ["string"],
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 6.4 `list-profiles`

Lists profiles. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-profiles \
    [--profile-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-type` | No | string | None | Filter by `LOCAL` or `PARTNER` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Profiles": [
        {
            "Arn": "string",
            "ProfileId": "string",
            "ProfileType": "LOCAL|PARTNER",
            "As2Id": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-profile`

Updates a profile's certificate associations.

**Synopsis:**
```bash
aws transfer update-profile \
    --profile-id <value> \
    [--certificate-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--profile-id` | **Yes** | string | -- | Profile ID |
| `--certificate-ids` | No | list(string) | None | Updated certificate IDs |

**Output Schema:**
```json
{
    "ProfileId": "string"
}
```
