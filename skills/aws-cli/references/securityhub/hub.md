# Hub

### 1.1 `enable-security-hub`

Enables Security Hub for the calling account in the current Region.

**Synopsis:**
```bash
aws securityhub enable-security-hub \
    [--tags <value>] \
    [--enable-default-standards | --no-enable-default-standards] \
    [--control-finding-generator <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | No | map | None | Tags to add (max 50, keys 1-128 chars, values max 256 chars) |
| `--enable-default-standards` / `--no-enable-default-standards` | No | boolean | true | Whether to enable default security standards |
| `--control-finding-generator` | No | string | None | Finding generation mode: `STANDARD_CONTROL` or `SECURITY_CONTROL` |

**Output:** None (HTTP 200 on success)

---

### 1.2 `disable-security-hub`

Disables Security Hub in the calling account. When disabled, findings and insights are not deleted but are no longer updated.

**Synopsis:**
```bash
aws securityhub disable-security-hub \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None (HTTP 200 on success)

---

### 1.3 `describe-hub`

Returns details about the Security Hub configuration for the calling account.

**Synopsis:**
```bash
aws securityhub describe-hub \
    [--hub-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hub-arn` | No | string | None | ARN of the hub resource to describe |

**Output Schema:**
```json
{
    "HubArn": "string",
    "SubscribedAt": "string",
    "AutoEnableControls": "boolean",
    "ControlFindingGenerator": "STANDARD_CONTROL|SECURITY_CONTROL"
}
```

---

### 1.4 `update-security-hub-configuration`

Updates Security Hub configuration.

**Synopsis:**
```bash
aws securityhub update-security-hub-configuration \
    [--auto-enable-controls | --no-auto-enable-controls] \
    [--control-finding-generator <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-enable-controls` / `--no-auto-enable-controls` | No | boolean | None | Automatically enable new controls in enabled standards |
| `--control-finding-generator` | No | string | None | Finding generation mode: `STANDARD_CONTROL` or `SECURITY_CONTROL` |

**Output:** None (HTTP 200 on success)
