# Encoder & Storage Configurations (Real-Time)

## Encoder Configurations

### 10.1 `create-encoder-configuration`

Creates an encoder configuration defining video output properties for compositions.

**Synopsis:**
```bash
aws ivs-realtime create-encoder-configuration \
    [--name <value>] \
    [--video <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Name (0-128 chars) |
| `--video` | No | structure | None | Video encoding properties |
| `--tags` | No | map | None | Key-value tag pairs |

**Video Structure:**
```json
{
    "width": 1280,
    "height": 720,
    "framerate": 30.0,
    "bitrate": 2500000
}
```

**Output Schema:**
```json
{
    "encoderConfiguration": {
        "arn": "string",
        "name": "string",
        "video": {
            "width": "integer",
            "height": "integer",
            "framerate": "float",
            "bitrate": "integer"
        },
        "tags": {"string": "string"}
    }
}
```

---

### 10.2 `get-encoder-configuration` / `list-encoder-configurations` / `delete-encoder-configuration`

Standard CRUD operations. `get` and `delete` require `--arn`. `list` supports `--next-token` and `--max-results`.

---

## Storage Configurations

### 10.3 `create-storage-configuration`

Creates a storage configuration pointing to an S3 bucket for recording.

**Synopsis:**
```bash
aws ivs-realtime create-storage-configuration \
    --s3 <value> \
    [--name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3` | **Yes** | structure | -- | S3 bucket configuration |
| `--name` | No | string | None | Name (0-128 chars) |
| `--tags` | No | map | None | Key-value tag pairs |

**S3 Structure:**
```json
{
    "bucketName": "my-recording-bucket"
}
```

**Output Schema:**
```json
{
    "storageConfiguration": {
        "arn": "string",
        "name": "string",
        "s3": {"bucketName": "string"},
        "tags": {"string": "string"}
    }
}
```

---

### 10.4 `get-storage-configuration` / `list-storage-configurations` / `delete-storage-configuration`

Standard CRUD operations. `get` and `delete` require `--arn`. `list` supports `--next-token` and `--max-results`.

---

## Public Keys

### 10.5 `import-public-key`

Imports a public key for token signing.

**Synopsis:**
```bash
aws ivs-realtime import-public-key \
    --public-key-material <value> \
    [--name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--public-key-material` | **Yes** | string | -- | PEM-encoded public key |
| `--name` | No | string | None | Key name |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "publicKey": {
        "arn": "string",
        "name": "string",
        "publicKeyMaterial": "string",
        "fingerprint": "string",
        "tags": {"string": "string"}
    }
}
```

---

### 10.6 `get-public-key` / `list-public-keys` / `delete-public-key`

Standard CRUD operations. `get` and `delete` require `--arn`. `list` supports `--next-token` and `--max-results`.
