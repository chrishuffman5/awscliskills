# Policies

### 4.1 `create-load-balancer-policy`

Creates a policy with the specified attributes for the specified load balancer.

**Synopsis:**
```bash
aws elb create-load-balancer-policy \
    --load-balancer-name <value> \
    --policy-name <value> \
    --policy-type-name <value> \
    [--policy-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--policy-name` | **Yes** | string | -- | Name of the policy (unique within the load balancer) |
| `--policy-type-name` | **Yes** | string | -- | Name of the policy type (e.g., `SSLNegotiationPolicyType`, `ProxyProtocolPolicyType`) |
| `--policy-attributes` | No | list | None | Policy attributes. Shorthand: `AttributeName=string,AttributeValue=string ...` |

**Output Schema:**
```json
{}
```

---

### 4.2 `delete-load-balancer-policy`

Deletes the specified policy from the specified load balancer. The policy must not be enabled for any listeners.

**Synopsis:**
```bash
aws elb delete-load-balancer-policy \
    --load-balancer-name <value> \
    --policy-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--policy-name` | **Yes** | string | -- | Name of the policy to delete |

**Output Schema:**
```json
{}
```

---

### 4.3 `describe-load-balancer-policies`

Describes the specified policies. If no policy names are specified, describes all policies defined for the load balancer. If no load balancer name is specified, describes all sample policies.

**Synopsis:**
```bash
aws elb describe-load-balancer-policies \
    [--load-balancer-name <value>] \
    [--policy-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | No | string | None | Name of the load balancer |
| `--policy-names` | No | list(string) | None | Names of the policies to describe |

**Output Schema:**
```json
{
    "PolicyDescriptions": [
        {
            "PolicyName": "string",
            "PolicyTypeName": "string",
            "PolicyAttributeDescriptions": [
                {
                    "AttributeName": "string",
                    "AttributeValue": "string"
                }
            ]
        }
    ]
}
```

---

### 4.4 `describe-load-balancer-policy-types`

Describes the specified load balancer policy types or all available policy types.

**Synopsis:**
```bash
aws elb describe-load-balancer-policy-types \
    [--policy-type-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-type-names` | No | list(string) | None | Names of the policy types to describe |

**Output Schema:**
```json
{
    "PolicyTypeDescriptions": [
        {
            "PolicyTypeName": "string",
            "Description": "string",
            "PolicyAttributeTypeDescriptions": [
                {
                    "AttributeName": "string",
                    "AttributeType": "string",
                    "Description": "string",
                    "DefaultValue": "string",
                    "Cardinality": "ONE|ZERO_OR_ONE|ZERO_OR_MORE|ONE_OR_MORE"
                }
            ]
        }
    ]
}
```

---

### 4.5 `create-app-cookie-stickiness-policy`

Generates a stickiness policy with sticky session lifetimes that follow an application-generated cookie. The load balancer uses this cookie to route requests from the same user to the same backend instance.

**Synopsis:**
```bash
aws elb create-app-cookie-stickiness-policy \
    --load-balancer-name <value> \
    --policy-name <value> \
    --cookie-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--policy-name` | **Yes** | string | -- | Name of the policy |
| `--cookie-name` | **Yes** | string | -- | Name of the application cookie used for stickiness |

**Output Schema:**
```json
{}
```

---

### 4.6 `create-lb-cookie-stickiness-policy`

Generates a stickiness policy with sticky session lifetimes controlled by the lifetime of the browser (user-agent) or a specified expiration period.

**Synopsis:**
```bash
aws elb create-lb-cookie-stickiness-policy \
    --load-balancer-name <value> \
    --policy-name <value> \
    [--cookie-expiration-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--policy-name` | **Yes** | string | -- | Name of the policy |
| `--cookie-expiration-period` | No | long | None | Time period in seconds after which the cookie expires. If not specified, the cookie lasts for the duration of the browser session |

**Output Schema:**
```json
{}
```

---

### 4.7 `set-load-balancer-policies-of-listener`

Replaces the current set of policies for the specified load balancer port with the specified set of policies. To enable back-end server authentication, use `set-load-balancer-policies-for-backend-server`.

**Synopsis:**
```bash
aws elb set-load-balancer-policies-of-listener \
    --load-balancer-name <value> \
    --load-balancer-port <value> \
    --policy-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--load-balancer-port` | **Yes** | integer | -- | External port of the load balancer |
| `--policy-names` | **Yes** | list(string) | -- | Names of the policies to set. Pass empty list to clear all policies |

**Output Schema:**
```json
{}
```

---

### 4.8 `set-load-balancer-policies-for-backend-server`

Replaces the current set of policies for the specified backend server port. Used to enable back-end server authentication.

**Synopsis:**
```bash
aws elb set-load-balancer-policies-for-backend-server \
    --load-balancer-name <value> \
    --instance-port <value> \
    --policy-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instance-port` | **Yes** | integer | -- | Port number of the backend server |
| `--policy-names` | **Yes** | list(string) | -- | Names of the policies to set. Pass empty list to clear all policies |

**Output Schema:**
```json
{}
```
