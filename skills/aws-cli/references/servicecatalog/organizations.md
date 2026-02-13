# Organizations

### 11.1 `enable-aws-organizations-access`

Enables portfolio sharing through AWS Organizations. This allows portfolios to be shared with all accounts in the organization or specific organizational units.

**Synopsis:**
```bash
aws servicecatalog enable-aws-organizations-access \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No additional parameters required.

**Output Schema:**
```json
{}
```

---

### 11.2 `disable-aws-organizations-access`

Disables portfolio sharing through AWS Organizations.

**Synopsis:**
```bash
aws servicecatalog disable-aws-organizations-access \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No additional parameters required.

**Output Schema:**
```json
{}
```

---

### 11.3 `get-aws-organizations-access-status`

Gets the status of whether AWS Organizations access is enabled for the account.

**Synopsis:**
```bash
aws servicecatalog get-aws-organizations-access-status \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No additional parameters required.

**Output Schema:**
```json
{
    "AccessStatus": "ENABLED|UNDER_CHANGE|DISABLED"
}
```
