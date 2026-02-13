# Studio Lifecycle

## 1. `create-studio-lifecycle-config`

Creates a Studio lifecycle configuration script that runs on startup of Studio apps.

**Synopsis:**
```bash
aws sagemaker create-studio-lifecycle-config \
    --studio-lifecycle-config-name <value> \
    --studio-lifecycle-config-content <value> \
    --studio-lifecycle-config-app-type <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-lifecycle-config-name` | **Yes** | string | -- | Config name (max 63 chars, `[a-zA-Z0-9](-*[a-zA-Z0-9])*`) |
| `--studio-lifecycle-config-content` | **Yes** | string | -- | Base64-encoded shell script content (max 16384 chars) |
| `--studio-lifecycle-config-app-type` | **Yes** | string | -- | `JupyterServer`, `KernelGateway`, `CodeEditor`, `JupyterLab` |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "StudioLifecycleConfigArn": "string"
}
```

---

## 2. `describe-studio-lifecycle-config`

Returns details about a Studio lifecycle configuration.

```bash
aws sagemaker describe-studio-lifecycle-config \
    --studio-lifecycle-config-name <value>
```

**Output Schema:**
```json
{
    "StudioLifecycleConfigArn": "string",
    "StudioLifecycleConfigName": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "StudioLifecycleConfigContent": "string",
    "StudioLifecycleConfigAppType": "JupyterServer|KernelGateway|CodeEditor|JupyterLab"
}
```

---

## 3. `list-studio-lifecycle-configs`

Lists Studio lifecycle configurations. **Paginated operation.**

```bash
aws sagemaker list-studio-lifecycle-configs \
    [--name-contains <value>] \
    [--app-type-equals <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--modified-time-before <value>] \
    [--modified-time-after <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-contains` | No | string | -- | Filter by name substring |
| `--app-type-equals` | No | string | -- | `JupyterServer`, `KernelGateway`, `CodeEditor`, `JupyterLab` |
| `--sort-by` | No | string | -- | `CreationTime`, `LastModifiedTime`, `Name` |
| `--sort-order` | No | string | -- | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "StudioLifecycleConfigs": [
        {
            "StudioLifecycleConfigArn": "string",
            "StudioLifecycleConfigName": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "StudioLifecycleConfigAppType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `delete-studio-lifecycle-config`

Deletes a Studio lifecycle configuration.

```bash
aws sagemaker delete-studio-lifecycle-config \
    --studio-lifecycle-config-name <value>
```

**Output:** None
