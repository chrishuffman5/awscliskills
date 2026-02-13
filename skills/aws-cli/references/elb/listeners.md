# Listeners

### 2.1 `create-load-balancer-listeners`

Creates one or more listeners for the specified load balancer. If a listener with the specified port already exists, the call fails.

**Synopsis:**
```bash
aws elb create-load-balancer-listeners \
    --load-balancer-name <value> \
    --listeners <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--listeners` | **Yes** | list | -- | Listeners to create. Shorthand: `Protocol=string,LoadBalancerPort=integer,InstanceProtocol=string,InstancePort=integer,SSLCertificateId=string ...` |

**Listener Structure:**
```json
[
    {
        "Protocol": "HTTP|HTTPS|TCP|SSL",
        "LoadBalancerPort": "integer",
        "InstanceProtocol": "HTTP|HTTPS|TCP|SSL",
        "InstancePort": "integer",
        "SSLCertificateId": "string"
    }
]
```

**Output Schema:**
```json
{}
```

---

### 2.2 `delete-load-balancer-listeners`

Deletes the specified listeners from the specified load balancer.

**Synopsis:**
```bash
aws elb delete-load-balancer-listeners \
    --load-balancer-name <value> \
    --load-balancer-ports <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--load-balancer-ports` | **Yes** | list(integer) | -- | Port numbers of the listeners to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `set-load-balancer-listener-ssl-certificate`

Sets the certificate that terminates the specified listener's SSL connections. The specified certificate replaces any prior certificate.

**Synopsis:**
```bash
aws elb set-load-balancer-listener-ssl-certificate \
    --load-balancer-name <value> \
    --load-balancer-port <value> \
    --ssl-certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--load-balancer-port` | **Yes** | integer | -- | Port of the listener (must be HTTPS or SSL) |
| `--ssl-certificate-id` | **Yes** | string | -- | ARN of the SSL certificate (ACM or IAM) |

**Output Schema:**
```json
{}
```
