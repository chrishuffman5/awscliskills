# Subscription

### 1.1 `create-subscription`

Activates AWS Shield Advanced for the calling account. Shield Advanced provides enhanced DDoS protection.

**Synopsis:**
```bash
aws shield create-subscription \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:** Empty on success.

---

### 1.2 `describe-subscription`

Returns the details of the current Shield Advanced subscription.

**Synopsis:**
```bash
aws shield describe-subscription \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "Subscription": {
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "TimeCommitmentInSeconds": "long",
        "AutoRenew": "ENABLED|DISABLED",
        "Limits": [
            {
                "Type": "string",
                "Max": "long"
            }
        ],
        "ProactiveEngagementStatus": "ENABLED|DISABLED|PENDING",
        "SubscriptionLimits": {
            "ProtectionLimits": {
                "ProtectedResourceTypeLimits": [
                    {
                        "Type": "string",
                        "Max": "long"
                    }
                ]
            },
            "ProtectionGroupLimits": {
                "MaxProtectionGroups": "long",
                "PatternTypeLimits": {
                    "ArbitraryPatternLimits": {
                        "MaxMembers": "long"
                    }
                }
            }
        },
        "SubscriptionArn": "string"
    }
}
```

---

### 1.3 `update-subscription`

Updates the auto-renew setting of the Shield Advanced subscription.

**Synopsis:**
```bash
aws shield update-subscription \
    [--auto-renew <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-renew` | No | string | None | Auto-renew setting: `ENABLED`, `DISABLED` |

**Output Schema:** Empty on success.

---

### 1.4 `get-subscription-state`

Returns the subscription state of the account (active or inactive).

**Synopsis:**
```bash
aws shield get-subscription-state \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "SubscriptionState": "ACTIVE|INACTIVE"
}
```
