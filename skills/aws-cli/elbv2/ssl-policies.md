# SSL Policies

### 6.1 `describe-ssl-policies`

Describes the specified SSL/TLS policies or all policies. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-ssl-policies \
    [--names <value>] \
    [--load-balancer-type <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list | -- | Names of SSL policies |
| `--load-balancer-type` | No | string | -- | Filter by LB type: `application`, `network`, `gateway` |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "SslPolicies": [
        {
            "Name": "string",
            "SslProtocols": ["string"],
            "Ciphers": [
                {
                    "Name": "string",
                    "Priority": integer
                }
            ],
            "SupportedLoadBalancerTypes": ["string"]
        }
    ],
    "NextMarker": "string"
}
```

---
