# Tags & Session

## Tags (`aws qldb`)

### 4.1 `tag-resource`

Adds one or more tags to a specified QLDB resource. A resource can have up to 50 tags.

**Synopsis:**
```bash
aws qldb tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the QLDB resource (ledger or stream) |
| `--tags` | **Yes** | map | -- | Key-value tag pairs. Shorthand: `KeyName1=string,KeyName2=string` |

**Output:** None (HTTP 200 on success)

---

### 4.2 `untag-resource`

Removes one or more tags from a specified QLDB resource.

**Synopsis:**
```bash
aws qldb untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the QLDB resource |
| `--tag-keys` | **Yes** | list(string) | -- | List of tag keys to remove |

**Output:** None (HTTP 200 on success)

---

### 4.3 `list-tags-for-resource`

Returns all tags for a specified QLDB resource.

**Synopsis:**
```bash
aws qldb list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the QLDB resource |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```

---

## Session (`aws qldb-session`)

### 4.4 `send-command`

Sends a command to a QLDB ledger. This is a low-level data plane API. AWS recommends using the QLDB driver or the QLDB shell instead of calling this API directly.

The `send-command` API supports the following operations within a session: `StartSession`, `StartTransaction`, `ExecuteStatement`, `CommitTransaction`, `AbortTransaction`, `EndSession`, and `FetchPage`.

**Synopsis:**
```bash
aws qldb-session send-command \
    [--session-token <value>] \
    [--start-session <value>] \
    [--start-transaction <value>] \
    [--end-session <value>] \
    [--commit-transaction <value>] \
    [--abort-transaction <value>] \
    [--execute-statement <value>] \
    [--fetch-page <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-token` | No | string | None | Session token for the current command (returned by StartSession; required for all subsequent commands) |
| `--start-session` | No | structure | None | Start a new session. Shorthand: `LedgerName=string` |
| `--start-transaction` | No | structure | None | Start a new transaction within the session (empty structure) |
| `--end-session` | No | structure | None | End the current session (empty structure) |
| `--commit-transaction` | No | structure | None | Commit the current transaction |
| `--abort-transaction` | No | structure | None | Abort the current transaction (empty structure) |
| `--execute-statement` | No | structure | None | Execute a PartiQL statement |
| `--fetch-page` | No | structure | None | Fetch the next page of results |

**Commit Transaction Structure:**
```json
{
    "TransactionId": "string",
    "CommitDigest": "blob"
}
```

**Execute Statement Structure:**
```json
{
    "TransactionId": "string",
    "Statement": "string",
    "Parameters": [
        {
            "IonBinary": "blob",
            "IonText": "string"
        }
    ]
}
```

**Fetch Page Structure:**
```json
{
    "TransactionId": "string",
    "NextPageToken": "string"
}
```

**Output Schema:**
```json
{
    "StartSession": {
        "SessionToken": "string",
        "TimingInformation": {
            "ProcessingTimeMilliseconds": "long"
        }
    },
    "StartTransaction": {
        "TransactionId": "string",
        "TimingInformation": {
            "ProcessingTimeMilliseconds": "long"
        }
    },
    "EndSession": {
        "TimingInformation": {
            "ProcessingTimeMilliseconds": "long"
        }
    },
    "CommitTransaction": {
        "TransactionId": "string",
        "CommitDigest": "blob",
        "TimingInformation": {
            "ProcessingTimeMilliseconds": "long"
        },
        "ConsumedIOs": {
            "ReadIOs": "long",
            "WriteIOs": "long"
        }
    },
    "AbortTransaction": {
        "TimingInformation": {
            "ProcessingTimeMilliseconds": "long"
        }
    },
    "ExecuteStatement": {
        "FirstPage": {
            "Values": [
                {
                    "IonBinary": "blob",
                    "IonText": "string"
                }
            ],
            "NextPageToken": "string"
        },
        "TimingInformation": {
            "ProcessingTimeMilliseconds": "long"
        },
        "ConsumedIOs": {
            "ReadIOs": "long",
            "WriteIOs": "long"
        }
    },
    "FetchPage": {
        "Page": {
            "Values": [
                {
                    "IonBinary": "blob",
                    "IonText": "string"
                }
            ],
            "NextPageToken": "string"
        },
        "TimingInformation": {
            "ProcessingTimeMilliseconds": "long"
        },
        "ConsumedIOs": {
            "ReadIOs": "long",
            "WriteIOs": "long"
        }
    }
}
```
