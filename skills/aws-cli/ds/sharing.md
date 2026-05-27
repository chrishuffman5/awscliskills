# Sharing

### 10.1 `share-directory`

Shares a Managed Microsoft AD directory with another AWS account.

**Synopsis:**
```bash
aws ds share-directory \
    --directory-id <value> \
    --share-target <value> \
    --share-method <value> \
    [--share-notes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID to share |
| `--share-target` | **Yes** | structure | -- | Target account. Structure: `Id=string,Type=ACCOUNT` |
| `--share-method` | **Yes** | string | -- | `ORGANIZATIONS` or `HANDSHAKE` |
| `--share-notes` | No | string | None | Message for the consumer (max 1024 chars, HANDSHAKE only) |

**Output Schema:**
```json
{
    "SharedDirectoryId": "string"
}
```

---

### 10.2 `unshare-directory`

Stops sharing a directory with another account.

**Synopsis:**
```bash
aws ds unshare-directory \
    --directory-id <value> \
    --unshare-target <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID to unshare |
| `--unshare-target` | **Yes** | structure | -- | Target account. Structure: `Id=string,Type=ACCOUNT` |

**Output Schema:**
```json
{
    "SharedDirectoryId": "string"
}
```

---

### 10.3 `accept-shared-directory`

Accepts a shared directory invitation from the owner account.

**Synopsis:**
```bash
aws ds accept-shared-directory \
    --shared-directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--shared-directory-id` | **Yes** | string | -- | ID of the shared directory in the consumer account |

**Output Schema:**
```json
{
    "SharedDirectory": {
        "OwnerAccountId": "string",
        "OwnerDirectoryId": "string",
        "ShareMethod": "ORGANIZATIONS|HANDSHAKE",
        "SharedAccountId": "string",
        "SharedDirectoryId": "string",
        "ShareStatus": "Shared|PendingAcceptance|Rejected|Rejecting|RejectFailed|Sharing|ShareFailed|Deleted|Deleting",
        "ShareNotes": "string",
        "CreatedDateTime": "timestamp",
        "LastUpdatedDateTime": "timestamp"
    }
}
```

---

### 10.4 `reject-shared-directory`

Rejects a shared directory invitation.

**Synopsis:**
```bash
aws ds reject-shared-directory \
    --shared-directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--shared-directory-id` | **Yes** | string | -- | ID of the shared directory to reject |

**Output Schema:**
```json
{
    "SharedDirectoryId": "string"
}
```

---

### 10.5 `describe-shared-directories`

Returns information about shared directories in your account. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-shared-directories \
    --owner-directory-id <value> \
    [--shared-directory-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--owner-directory-id` | **Yes** | string | -- | Directory ID of the owner directory |
| `--shared-directory-ids` | No | list(string) | All | Filter by shared directory IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SharedDirectories": [
        {
            "OwnerAccountId": "string",
            "OwnerDirectoryId": "string",
            "ShareMethod": "ORGANIZATIONS|HANDSHAKE",
            "SharedAccountId": "string",
            "SharedDirectoryId": "string",
            "ShareStatus": "Shared|PendingAcceptance|Rejected|Rejecting|RejectFailed|Sharing|ShareFailed|Deleted|Deleting",
            "ShareNotes": "string",
            "CreatedDateTime": "timestamp",
            "LastUpdatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
