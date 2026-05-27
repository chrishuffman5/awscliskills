# Organization Access

### 4.1 `enable-health-service-access-for-organization`

Enables Health to work with AWS Organizations to aggregate Health events from all member accounts. Must be called from the management account.

**Synopsis:**
```bash
aws health enable-health-service-access-for-organization \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output:** None

> Requires a Business, Enterprise On-Ramp, or Enterprise Support plan from AWS Support.

---

### 4.2 `disable-health-service-access-for-organization`

Disables Health organizational view. Stops aggregation of events from organization member accounts.

**Synopsis:**
```bash
aws health disable-health-service-access-for-organization \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output:** None

> After disabling, you can no longer call the organization-level operations (`describe-events-for-organization`, `describe-affected-entities-for-organization`, etc.) from this account.

---

### 4.3 `describe-health-service-status-for-organization`

Returns the status of Health organizational view: whether it is enabled or not.

**Synopsis:**
```bash
aws health describe-health-service-status-for-organization \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "healthServiceAccessStatusForOrganization": "string"
}
```

| Value | Description |
|-------|-------------|
| `ENABLED` | Health organizational view is enabled |
| `DISABLED` | Health organizational view is disabled |
| `PENDING` | Health organizational view is being enabled |
