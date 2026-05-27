# Third-Party Firewalls

### 5.1 `associate-third-party-firewall`

Sets the Firewall Manager policy administrator as a tenant administrator of a third-party firewall service.

**Synopsis:**
```bash
aws fms associate-third-party-firewall \
    --third-party-firewall <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--third-party-firewall` | **Yes** | string | -- | Third-party firewall: `PALO_ALTO_NETWORKS_CLOUD_NGFW`, `FORTIGATE_CLOUD_NATIVE_FIREWALL` |

**Output Schema:**
```json
{
    "ThirdPartyFirewallStatus": "ONBOARDING|ONBOARD_COMPLETE|OFFBOARDING|OFFBOARD_COMPLETE|NOT_EXIST"
}
```

---

### 5.2 `disassociate-third-party-firewall`

Removes the Firewall Manager policy administrator as a tenant administrator of a third-party firewall service.

**Synopsis:**
```bash
aws fms disassociate-third-party-firewall \
    --third-party-firewall <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--third-party-firewall` | **Yes** | string | -- | Third-party firewall: `PALO_ALTO_NETWORKS_CLOUD_NGFW`, `FORTIGATE_CLOUD_NATIVE_FIREWALL` |

**Output Schema:**
```json
{
    "ThirdPartyFirewallStatus": "ONBOARDING|ONBOARD_COMPLETE|OFFBOARDING|OFFBOARD_COMPLETE|NOT_EXIST"
}
```

---

### 5.3 `get-third-party-firewall-association-status`

Gets the current association status of a third-party firewall.

**Synopsis:**
```bash
aws fms get-third-party-firewall-association-status \
    --third-party-firewall <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--third-party-firewall` | **Yes** | string | -- | Third-party firewall: `PALO_ALTO_NETWORKS_CLOUD_NGFW`, `FORTIGATE_CLOUD_NATIVE_FIREWALL` |

**Output Schema:**
```json
{
    "ThirdPartyFirewallStatus": "ONBOARDING|ONBOARD_COMPLETE|OFFBOARDING|OFFBOARD_COMPLETE|NOT_EXIST",
    "MarketplaceOnboardingStatus": "NO_SUBSCRIPTION|NOT_COMPLETE|COMPLETE"
}
```

---

### 5.4 `list-third-party-firewall-firewall-policies`

Lists the third-party firewall policies that can be used in Firewall Manager policies. **Paginated.**

**Synopsis:**
```bash
aws fms list-third-party-firewall-firewall-policies \
    --third-party-firewall <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--third-party-firewall` | **Yes** | string | -- | Third-party firewall: `PALO_ALTO_NETWORKS_CLOUD_NGFW`, `FORTIGATE_CLOUD_NATIVE_FIREWALL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ThirdPartyFirewallFirewallPolicies": [
        {
            "FirewallPolicyId": "string",
            "FirewallPolicyName": "string"
        }
    ],
    "NextToken": "string"
}
```
