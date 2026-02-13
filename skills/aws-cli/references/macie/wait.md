# Wait

The `aws macie2 wait` subcommand blocks until a resource reaches a specific state, polling at regular intervals.

### 14.1 `wait finding-revealed`

Waits until sensitive data occurrences for a finding are available for retrieval. Polls `get-sensitive-data-occurrences-availability` every 2 seconds until it reaches a successful state, with a maximum of 60 attempts.

**Synopsis:**
```bash
aws macie2 wait finding-revealed \
    --finding-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-id` | **Yes** | string | -- | Finding ID to wait for |

**Output:** None (exits with 0 on success, 255 on failure/timeout)

**Behavior:**
- **Polling interval:** 2 seconds
- **Max attempts:** 60
- **Success condition:** `get-sensitive-data-occurrences-availability` returns `code` of `AVAILABLE`
- **Failure condition:** Max attempts exceeded or an unexpected error occurs

**Example:**
```bash
# Wait for sensitive data to be available, then retrieve it
aws macie2 wait finding-revealed --finding-id abc123
aws macie2 get-sensitive-data-occurrences --finding-id abc123
```
