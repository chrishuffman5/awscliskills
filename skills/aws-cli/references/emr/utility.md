# Utility Commands

### 10.1 `ssh`

Opens an SSH connection to the master node of a cluster.

**Synopsis:**
```bash
aws emr ssh \
    --cluster-id <value> \
    --key-pair-file <value> \
    [--command <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--key-pair-file` | **Yes** | string | -- | Path to the private key file |
| `--command` | No | string | -- | Command to execute on the master node |

Opens an interactive SSH session or runs the specified command.

---

### 10.2 `socks`

Creates a SOCKS proxy to the master node for accessing web UIs.

**Synopsis:**
```bash
aws emr socks \
    --cluster-id <value> \
    --key-pair-file <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--key-pair-file` | **Yes** | string | -- | Path to the private key file |

Opens a SOCKS proxy tunnel (typically on port 8157).

---

### 10.3 `get`

Downloads a file from the master node.

**Synopsis:**
```bash
aws emr get \
    --cluster-id <value> \
    --key-pair-file <value> \
    --src <value> \
    [--dest <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--key-pair-file` | **Yes** | string | -- | Path to the private key file |
| `--src` | **Yes** | string | -- | Remote path on the master node |
| `--dest` | No | string | `.` | Local destination path |

Downloads the file via SCP.

---

### 10.4 `put`

Uploads a file to the master node.

**Synopsis:**
```bash
aws emr put \
    --cluster-id <value> \
    --key-pair-file <value> \
    --src <value> \
    [--dest <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--key-pair-file` | **Yes** | string | -- | Path to the private key file |
| `--src` | **Yes** | string | -- | Local file path |
| `--dest` | No | string | -- | Remote destination path on master |

Uploads the file via SCP.

---

### 10.5 `add-tags`

Adds tags to an EMR resource.

**Synopsis:**
```bash
aws emr add-tags \
    --resource-id <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Resource ID (cluster, etc.) |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string` or `key=value` |

No output on success.

---

### 10.6 `remove-tags`

Removes tags from an EMR resource.

**Synopsis:**
```bash
aws emr remove-tags \
    --resource-id <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

No output on success.
