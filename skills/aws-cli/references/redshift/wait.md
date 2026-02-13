# Wait Commands

The `aws redshift wait` subcommand blocks until a resource reaches a specific state. Each waiter polls at a fixed interval and has a maximum number of attempts.

---

### 19.1 `wait cluster-available`

Polls `describe-clusters` every 60 seconds until the cluster status is `available`. Fails after 30 attempts (30 minutes).

**Synopsis:**
```bash
aws redshift wait cluster-available \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | No | string | -- | Cluster to wait for (or omit to wait for all) |

**Example:**
```bash
aws redshift wait cluster-available --cluster-identifier my-cluster
```

---

### 19.2 `wait cluster-deleted`

Polls `describe-clusters` every 60 seconds until the cluster is deleted (returns 404). Fails after 30 attempts (30 minutes).

**Synopsis:**
```bash
aws redshift wait cluster-deleted \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | No | string | -- | Cluster to wait for deletion |

**Example:**
```bash
aws redshift wait cluster-deleted --cluster-identifier my-cluster
```

---

### 19.3 `wait cluster-restored`

Polls `describe-clusters` every 60 seconds until a restored cluster reaches `available` status. Fails after 30 attempts (30 minutes).

**Synopsis:**
```bash
aws redshift wait cluster-restored \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | No | string | -- | Restored cluster to wait for |

**Example:**
```bash
aws redshift wait cluster-restored --cluster-identifier my-restored-cluster
```

---

### 19.4 `wait snapshot-available`

Polls `describe-cluster-snapshots` every 15 seconds until the snapshot status is `available`. Fails after 20 attempts (5 minutes).

**Synopsis:**
```bash
aws redshift wait snapshot-available \
    [--snapshot-identifier <value>] \
    [--cluster-identifier <value>] \
    [--snapshot-type <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | No | string | -- | Snapshot to wait for |
| `--cluster-identifier` | No | string | -- | Filter by cluster |
| `--snapshot-type` | No | string | -- | Filter: `automated` or `manual` |

**Example:**
```bash
aws redshift wait snapshot-available \
  --snapshot-identifier my-manual-snap \
  --cluster-identifier my-cluster
```
