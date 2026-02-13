# DRT Access

The DDoS Response Team (DRT) can assist during a DDoS attack. These commands manage the DRT's access to your account.

### 4.1 `associate-drt-role`

Authorizes the Shield Response Team (SRT) to access your account using the specified IAM role. You must have Shield Advanced subscription.

**Synopsis:**
```bash
aws shield associate-drt-role \
    --role-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | **Yes** | string | -- | ARN of the IAM role for DRT access |

**Output Schema:** Empty on success.

---

### 4.2 `disassociate-drt-role`

Removes the IAM role used by the DRT to access your account.

**Synopsis:**
```bash
aws shield disassociate-drt-role \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:** Empty on success.

---

### 4.3 `associate-drt-log-bucket`

Authorizes the DRT to access the specified S3 bucket containing flow logs or other relevant data for incident response.

**Synopsis:**
```bash
aws shield associate-drt-log-bucket \
    --log-bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-bucket` | **Yes** | string | -- | S3 bucket name (3-63 chars) |

**Output Schema:** Empty on success.

---

### 4.4 `disassociate-drt-log-bucket`

Removes DRT access to the specified S3 log bucket.

**Synopsis:**
```bash
aws shield disassociate-drt-log-bucket \
    --log-bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-bucket` | **Yes** | string | -- | S3 bucket name to remove access for |

**Output Schema:** Empty on success.

---

### 4.5 `describe-drt-access`

Returns the current DRT access configuration, including the IAM role and associated S3 log buckets.

**Synopsis:**
```bash
aws shield describe-drt-access \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "RoleArn": "string",
    "LogBucketList": ["string"]
}
```
