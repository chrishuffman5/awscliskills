# Playback

## Playback Key Pairs

### 5.1 `import-playback-key-pair`

Imports a public key for playback authorization (JWT token verification).

**Synopsis:**
```bash
aws ivs import-playback-key-pair \
    --public-key-material <value> \
    [--name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--public-key-material` | **Yes** | string | -- | PEM-encoded public key |
| `--name` | No | string | None | Key pair name |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "keyPair": {
        "arn": "string",
        "name": "string",
        "fingerprint": "string",
        "tags": {"string": "string"}
    }
}
```

---

### 5.2 `get-playback-key-pair`

Gets details for a playback key pair.

**Synopsis:**
```bash
aws ivs get-playback-key-pair --arn <value>
```

---

### 5.3 `list-playback-key-pairs`

Lists playback key pairs. **Paginated operation.**

**Synopsis:**
```bash
aws ivs list-playback-key-pairs \
    [--next-token <value>] \
    [--max-results <value>]
```

---

### 5.4 `delete-playback-key-pair`

Deletes a playback key pair.

**Synopsis:**
```bash
aws ivs delete-playback-key-pair --arn <value>
```

**Output:** None

---

## Playback Restriction Policies

### 5.5 `create-playback-restriction-policy`

Creates a policy to restrict playback by country or origin.

**Synopsis:**
```bash
aws ivs create-playback-restriction-policy \
    [--name <value>] \
    [--allowed-countries <value>] \
    [--allowed-origins <value>] \
    [--enable-strict-origin-enforcement | --no-enable-strict-origin-enforcement] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Policy name (0-128 chars) |
| `--allowed-countries` | No | list | None | ISO 3166-1 country codes allowed for playback |
| `--allowed-origins` | No | list | None | Allowed origin domains for playback |
| `--enable-strict-origin-enforcement` | No | boolean | false | Enforce strict origin checking |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "playbackRestrictionPolicy": {
        "arn": "string",
        "name": "string",
        "allowedCountries": ["string"],
        "allowedOrigins": ["string"],
        "enableStrictOriginEnforcement": "boolean",
        "tags": {"string": "string"}
    }
}
```

---

### 5.6 `get-playback-restriction-policy` / `list-playback-restriction-policies` / `update-playback-restriction-policy` / `delete-playback-restriction-policy`

Standard CRUD operations for playback restriction policies. `get` and `delete` require `--arn`. `update` requires `--arn` and accepts the same optional params as `create`.

---

## Viewer Session Revocation

### 5.7 `start-viewer-session-revocation`

Revokes a specific viewer's session, forcing them to re-authenticate.

**Synopsis:**
```bash
aws ivs start-viewer-session-revocation \
    --channel-arn <value> \
    --viewer-id <value> \
    [--viewer-session-versions-less-than-or-equal-to <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |
| `--viewer-id` | **Yes** | string | -- | ID of the viewer to revoke |
| `--viewer-session-versions-less-than-or-equal-to` | No | integer | None | Revoke sessions at or before this version |

**Output:** None

---

### 5.8 `batch-start-viewer-session-revocation`

Revokes multiple viewer sessions in a single call.

**Synopsis:**
```bash
aws ivs batch-start-viewer-session-revocation \
    --viewer-sessions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--viewer-sessions` | **Yes** | list | -- | List of viewer sessions to revoke |

**ViewerSession Structure:**
```json
[
    {
        "channelArn": "string",
        "viewerId": "string",
        "viewerSessionVersionsLessThanOrEqualTo": "integer"
    }
]
```

**Output Schema:**
```json
{
    "errors": [
        {"channelArn": "string", "viewerId": "string", "code": "string", "message": "string"}
    ]
}
```
