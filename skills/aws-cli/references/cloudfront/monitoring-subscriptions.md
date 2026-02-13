# Monitoring Subscriptions

### 14.1 `create-monitoring-subscription`

Enables additional CloudWatch metrics for a distribution.

**Synopsis:**
```bash
aws cloudfront create-monitoring-subscription \
    --distribution-id <value> \
    --monitoring-subscription <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-id` | **Yes** | string | Distribution ID |
| `--monitoring-subscription` | **Yes** | structure | `RealtimeMetricsSubscriptionConfig` with `RealtimeMetricsSubscriptionStatus`: `Enabled` or `Disabled` |

**Output Schema:**
```json
{
    "MonitoringSubscription": {
        "RealtimeMetricsSubscriptionConfig": {
            "RealtimeMetricsSubscriptionStatus": "Enabled|Disabled"
        }
    }
}
```

---

### 14.2 `get-monitoring-subscription`

Gets the monitoring subscription for a distribution.

**Synopsis:**
```bash
aws cloudfront get-monitoring-subscription \
    --distribution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-id` | **Yes** | string | Distribution ID |

**Output Schema:** Same as `create-monitoring-subscription`.

---

### 14.3 `delete-monitoring-subscription`

Disables additional CloudWatch metrics for a distribution.

**Synopsis:**
```bash
aws cloudfront delete-monitoring-subscription \
    --distribution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-id` | **Yes** | string | Distribution ID |

**Output:** None.

---
