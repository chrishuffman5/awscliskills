# Wait

### 11.1 `wait fleet-started`

Polls `describe-fleets` every 30 seconds until the fleet state is `RUNNING`. Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws appstream wait fleet-started \
    [--names <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | -- | Names of the fleets to wait for |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{}
```

---

### 11.2 `wait fleet-stopped`

Polls `describe-fleets` every 30 seconds until the fleet state is `STOPPED`. Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws appstream wait fleet-stopped \
    [--names <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | -- | Names of the fleets to wait for |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{}
```
