# Conditional Forwarders

### 4.1 `create-conditional-forwarder`

Creates a conditional forwarder for DNS resolution to an on-premises domain.

**Synopsis:**
```bash
aws ds create-conditional-forwarder \
    --directory-id <value> \
    --remote-domain-name <value> \
    --dns-ip-addrs <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--remote-domain-name` | **Yes** | string | -- | FQDN of the remote domain |
| `--dns-ip-addrs` | **Yes** | list(string) | -- | IP addresses of the remote DNS servers |

**Output Schema:**

No output on success (HTTP 200).

---

### 4.2 `delete-conditional-forwarder`

Deletes a conditional forwarder.

**Synopsis:**
```bash
aws ds delete-conditional-forwarder \
    --directory-id <value> \
    --remote-domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--remote-domain-name` | **Yes** | string | -- | FQDN of the remote domain |

**Output Schema:**

No output on success (HTTP 200).

---

### 4.3 `describe-conditional-forwarders`

Describes conditional forwarders for a directory.

**Synopsis:**
```bash
aws ds describe-conditional-forwarders \
    --directory-id <value> \
    [--remote-domain-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--remote-domain-names` | No | list(string) | All | Filter by remote domain names |

**Output Schema:**
```json
{
    "ConditionalForwarders": [
        {
            "RemoteDomainName": "string",
            "DnsIpAddrs": ["string"],
            "ReplicationScope": "Domain"
        }
    ]
}
```

---

### 4.4 `update-conditional-forwarder`

Updates a conditional forwarder's DNS IP addresses.

**Synopsis:**
```bash
aws ds update-conditional-forwarder \
    --directory-id <value> \
    --remote-domain-name <value> \
    --dns-ip-addrs <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--remote-domain-name` | **Yes** | string | -- | FQDN of the remote domain |
| `--dns-ip-addrs` | **Yes** | list(string) | -- | Updated DNS IP addresses |

**Output Schema:**

No output on success (HTTP 200).
