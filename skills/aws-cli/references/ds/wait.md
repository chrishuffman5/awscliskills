# Wait

The `aws ds wait` subcommand blocks until a directory reaches a specific state. It polls the `describe-directories` API every 30 seconds until the desired state is reached or the maximum number of attempts (40) is exceeded.

### 13.1 `wait directory-available`

Waits until a directory is in the `Active` state.

**Synopsis:**
```bash
aws ds wait directory-available \
    [--directory-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-ids` | No | list(string) | All | Directory IDs to wait for |

**Behavior:**
- Polls `describe-directories` every 30 seconds
- Succeeds when the directory `Stage` is `Active`
- Fails after 40 attempts (approximately 20 minutes)
- Exits with return code 255 on timeout

**Example:**
```bash
# Create a directory and wait for it to become active
aws ds create-microsoft-ad --name corp.example.com \
  --password 'MyP@ssw0rd!' \
  --vpc-settings VpcId=vpc-12345678,SubnetIds=subnet-aaaa1111,subnet-bbbb2222

aws ds wait directory-available --directory-ids d-1234567890
echo "Directory is now active"
```

**No output** on success. Exits with a non-zero return code on failure or timeout.
