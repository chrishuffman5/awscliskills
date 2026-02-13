# Wait Commands

The `aws eks wait` subcommand blocks until a resource reaches a specific state, polling at regular intervals.

---

### 12.1 `wait cluster-active`

Wait until a cluster reaches `ACTIVE` status. Polls `describe-cluster` every 30 seconds (max 40 attempts / 20 minutes).

**Synopsis:**
```bash
aws eks wait cluster-active \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.

---

### 12.2 `wait cluster-deleted`

Wait until a cluster is deleted. Polls `describe-cluster` every 30 seconds (max 40 attempts / 20 minutes).

**Synopsis:**
```bash
aws eks wait cluster-deleted \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.

---

### 12.3 `wait nodegroup-active`

Wait until a node group reaches `ACTIVE` status. Polls `describe-nodegroup` every 30 seconds (max 80 attempts / 40 minutes).

**Synopsis:**
```bash
aws eks wait nodegroup-active \
    --cluster-name <value> \
    --nodegroup-name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | **Yes** | string | -- | Node group name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.

---

### 12.4 `wait nodegroup-deleted`

Wait until a node group is deleted. Polls `describe-nodegroup` every 30 seconds (max 40 attempts / 20 minutes).

**Synopsis:**
```bash
aws eks wait nodegroup-deleted \
    --cluster-name <value> \
    --nodegroup-name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | **Yes** | string | -- | Node group name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.

---

### 12.5 `wait addon-active`

Wait until an add-on reaches `ACTIVE` status. Polls `describe-addon` every 10 seconds (max 60 attempts / 10 minutes).

**Synopsis:**
```bash
aws eks wait addon-active \
    --cluster-name <value> \
    --addon-name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--addon-name` | **Yes** | string | -- | Add-on name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.

---

### 12.6 `wait addon-deleted`

Wait until an add-on is deleted. Polls `describe-addon` every 10 seconds (max 60 attempts / 10 minutes).

**Synopsis:**
```bash
aws eks wait addon-deleted \
    --cluster-name <value> \
    --addon-name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--addon-name` | **Yes** | string | -- | Add-on name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.

---

### 12.7 `wait fargate-profile-active`

Wait until a Fargate profile reaches `ACTIVE` status. Polls `describe-fargate-profile` every 10 seconds (max 60 attempts / 10 minutes).

**Synopsis:**
```bash
aws eks wait fargate-profile-active \
    --cluster-name <value> \
    --fargate-profile-name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--fargate-profile-name` | **Yes** | string | -- | Fargate profile name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.

---

### 12.8 `wait fargate-profile-deleted`

Wait until a Fargate profile is deleted. Polls `describe-fargate-profile` every 30 seconds (max 60 attempts / 30 minutes).

**Synopsis:**
```bash
aws eks wait fargate-profile-deleted \
    --cluster-name <value> \
    --fargate-profile-name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--fargate-profile-name` | **Yes** | string | -- | Fargate profile name |

**Output:** No output. Exits 0 on success, 255 on failure or timeout.
