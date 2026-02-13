# Authentication

### 5.1 `get-authorization-token`

Retrieves an authorization token (base64-encoded `user:password`) valid for 12 hours.

**Synopsis:**
```bash
aws ecr get-authorization-token \
    [--registry-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-ids` | No | list(string) | caller's registry | 1-10 AWS account IDs. Pattern: `[0-9]{12}` |

**Output Schema:**
```json
{
    "authorizationData": [
        {
            "authorizationToken": "string",
            "expiresAt": "timestamp",
            "proxyEndpoint": "string"
        }
    ]
}
```

| Field | Description |
|-------|-------------|
| `authorizationToken` | Base64-encoded string in `user:password` format for `docker login` |
| `expiresAt` | Token expiration (valid 12 hours) |
| `proxyEndpoint` | Registry URL: `https://<account_id>.dkr.ecr.<region>.amazonaws.com` |

---

### 5.2 `get-login-password`

Retrieves a password for authenticating to an ECR registry. Preferred over `get-authorization-token` for Docker login.

**Synopsis:**
```bash
aws ecr get-login-password
```

**Parameters:** None (only global options).

**Output:** Returns a plain text password string (not JSON). Pipe directly to `docker login`:

```bash
aws ecr get-login-password --region us-east-1 | \
    docker login --username AWS --password-stdin \
    123456789012.dkr.ecr.us-east-1.amazonaws.com
```

> Token is valid for 12 hours.

---

