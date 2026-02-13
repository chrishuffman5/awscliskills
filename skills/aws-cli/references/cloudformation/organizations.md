# Organizations

### 10.1 `activate-organizations-access`

Activates trusted access with AWS Organizations. This allows you to create stack sets with `SERVICE_MANAGED` permission model.

**Synopsis:**
```bash
aws cloudformation activate-organizations-access \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output:** No output on success (empty JSON `{}`).

---

### 10.2 `deactivate-organizations-access`

Deactivates trusted access with AWS Organizations. After deactivation, you cannot create new stack sets with `SERVICE_MANAGED` permission model.

**Synopsis:**
```bash
aws cloudformation deactivate-organizations-access \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output:** No output on success (empty JSON `{}`).

---

### 10.3 `describe-organizations-access`

Returns information about the Organizations access status for CloudFormation.

**Synopsis:**
```bash
aws cloudformation describe-organizations-access \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "Status": "ACTIVE|DISABLED|DISABLED_PERMANENTLY"
}
```
