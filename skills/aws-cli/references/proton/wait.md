# Wait Commands

Proton provides built-in waiters that poll a resource until it reaches a desired state.

---

### 10.1 `wait environment-deployed`

Polls `get-environment` every 5 seconds until deployment completes. Exits with return code 255 after 999 failed checks.

**Synopsis:**
```bash
aws proton wait environment-deployed \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name |

**Success condition:** `deploymentStatus` is `SUCCEEDED`.

**Failure condition:** `deploymentStatus` is `FAILED`.

---

### 10.2 `wait environment-template-version-registered`

Polls `get-environment-template-version` every 2 seconds until registration completes. Exits with return code 255 after 150 failed checks.

**Synopsis:**
```bash
aws proton wait environment-template-version-registered \
    --template-name <value> \
    --major-version <value> \
    --minor-version <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--major-version` | **Yes** | string | -- | Major version |
| `--minor-version` | **Yes** | string | -- | Minor version |

**Success condition:** `status` is `DRAFT` or `PUBLISHED`.

**Failure condition:** `status` is `REGISTRATION_FAILED`.

---

### 10.3 `wait service-created`

Polls `get-service` every 5 seconds until service is created. Exits with return code 255 after 999 failed checks.

**Synopsis:**
```bash
aws proton wait service-created \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |

**Success condition:** `status` is `ACTIVE`.

**Failure conditions:** `status` is `CREATE_FAILED_CLEANUP_COMPLETE`, `CREATE_FAILED_CLEANUP_FAILED`, or `CREATE_FAILED`.

---

### 10.4 `wait service-deleted`

Polls `get-service` every 5 seconds until service is deleted. Exits with return code 255 after 999 failed checks.

**Synopsis:**
```bash
aws proton wait service-deleted \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |

**Success condition:** Error is `ResourceNotFoundException` (service no longer exists).

**Failure condition:** `status` is `DELETE_FAILED`.

---

### 10.5 `wait service-updated`

Polls `get-service` every 5 seconds until service update completes. Exits with return code 255 after 999 failed checks.

**Synopsis:**
```bash
aws proton wait service-updated \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |

**Success condition:** `status` is `ACTIVE`.

**Failure conditions:** `status` is `UPDATE_FAILED_CLEANUP_COMPLETE`, `UPDATE_FAILED_CLEANUP_FAILED`, `UPDATE_FAILED`, or `UPDATE_COMPLETE_CLEANUP_FAILED`.

---

### 10.6 `wait service-instance-deployed`

Polls `get-service-instance` every 5 seconds until deployment completes. Exits with return code 255 after 999 failed checks.

**Synopsis:**
```bash
aws proton wait service-instance-deployed \
    --name <value> \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service instance name |
| `--service-name` | **Yes** | string | -- | Service name |

**Success condition:** `deploymentStatus` is `SUCCEEDED`.

**Failure condition:** `deploymentStatus` is `FAILED`.

---

### 10.7 `wait service-pipeline-deployed`

Polls `get-service` every 10 seconds until service pipeline deployment completes. Exits with return code 255 after 360 failed checks.

**Synopsis:**
```bash
aws proton wait service-pipeline-deployed \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |

**Success condition:** `pipeline.deploymentStatus` is `SUCCEEDED`.

**Failure condition:** `pipeline.deploymentStatus` is `FAILED`.

---

### 10.8 `wait service-template-version-registered`

Polls `get-service-template-version` every 2 seconds until registration completes. Exits with return code 255 after 150 failed checks.

**Synopsis:**
```bash
aws proton wait service-template-version-registered \
    --template-name <value> \
    --major-version <value> \
    --minor-version <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--major-version` | **Yes** | string | -- | Major version |
| `--minor-version` | **Yes** | string | -- | Minor version |

**Success condition:** `status` is `DRAFT` or `PUBLISHED`.

**Failure condition:** `status` is `REGISTRATION_FAILED`.

---

### 10.9 `wait component-deployed`

Polls `get-component` every 5 seconds until deployment completes. Exits with return code 255 after 999 failed checks.

**Synopsis:**
```bash
aws proton wait component-deployed \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Component name |

**Success condition:** `deploymentStatus` is `SUCCEEDED`.

**Failure condition:** `deploymentStatus` is `FAILED`.

---

### 10.10 `wait component-deleted`

Polls `get-component` every 5 seconds until component is deleted. Exits with return code 255 after 999 failed checks.

**Synopsis:**
```bash
aws proton wait component-deleted \
    --name <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Component name |

**Success condition:** Error is `ResourceNotFoundException` (component no longer exists).

**Failure condition:** `deploymentStatus` is `DELETE_FAILED`.
