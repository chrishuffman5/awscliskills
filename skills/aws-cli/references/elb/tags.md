# Tags

### 6.1 `add-tags`

Adds the specified tags to the specified load balancer. Each load balancer can have a maximum of 10 tags.

**Synopsis:**
```bash
aws elb add-tags \
    --load-balancer-names <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-names` | **Yes** | list(string) | -- | Names of the load balancers to tag (one or more) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{}
```

---

### 6.2 `remove-tags`

Removes one or more tags from the specified load balancer.

**Synopsis:**
```bash
aws elb remove-tags \
    --load-balancer-names <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-names` | **Yes** | list(string) | -- | Names of the load balancers |
| `--tags` | **Yes** | list | -- | Tag keys to remove. Shorthand: `Key=string ...` |

**Output Schema:**
```json
{}
```

---

### 6.3 `describe-tags`

Describes the tags associated with the specified load balancers.

**Synopsis:**
```bash
aws elb describe-tags \
    --load-balancer-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-names` | **Yes** | list(string) | -- | Names of the load balancers (max 20) |

**Output Schema:**
```json
{
    "TagDescriptions": [
        {
            "LoadBalancerName": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ]
        }
    ]
}
```
