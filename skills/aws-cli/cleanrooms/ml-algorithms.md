# ML Algorithms

> Commands in this file use the `aws cleanroomsml` namespace.

## 14.1 `create-configured-model-algorithm`

Creates a configured model algorithm.

**Synopsis:**
```bash
aws cleanroomsml create-configured-model-algorithm \
    --name <value> \
    --role-arn <value> \
    [--description <value>] \
    [--training-container-config <value>] \
    [--inference-container-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Algorithm name |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--description` | No | string | None | Description |
| `--training-container-config` | No | structure | None | Training container configuration |
| `--inference-container-config` | No | list | None | Inference container configuration |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "configuredModelAlgorithmArn": "string"
}
```

---

## 14.2 `delete-configured-model-algorithm`

Deletes a configured model algorithm.

**Synopsis:**
```bash
aws cleanroomsml delete-configured-model-algorithm \
    --configured-model-algorithm-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-model-algorithm-arn` | **Yes** | string | -- | Algorithm ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 14.3 `get-configured-model-algorithm`

Returns details for a configured model algorithm.

**Synopsis:**
```bash
aws cleanroomsml get-configured-model-algorithm \
    --configured-model-algorithm-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-model-algorithm-arn` | **Yes** | string | -- | Algorithm ARN |

**Output Schema:**
```json
{
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "configuredModelAlgorithmArn": "string",
    "name": "string",
    "trainingContainerConfig": {
        "imageUri": "string",
        "entrypoint": ["string"],
        "arguments": ["string"],
        "metricDefinitions": []
    },
    "inferenceContainerConfig": [],
    "roleArn": "string",
    "description": "string",
    "tags": { "string": "string" }
}
```

---

## 14.4 `list-configured-model-algorithms`

Lists configured model algorithms. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-configured-model-algorithms \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "configuredModelAlgorithms": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "configuredModelAlgorithmArn": "string",
            "name": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 14.5 `create-configured-model-algorithm-association`

Associates a configured model algorithm with a membership in a collaboration.

**Synopsis:**
```bash
aws cleanroomsml create-configured-model-algorithm-association \
    --membership-identifier <value> \
    --configured-model-algorithm-arn <value> \
    --name <value> \
    [--description <value>] \
    [--privacy-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-model-algorithm-arn` | **Yes** | string | -- | Algorithm ARN |
| `--name` | **Yes** | string | -- | Association name |
| `--description` | No | string | None | Description |
| `--privacy-configuration` | No | structure | None | Privacy configuration |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "configuredModelAlgorithmAssociationArn": "string"
}
```

---

## 14.6 `delete-configured-model-algorithm-association`

Deletes an algorithm association.

**Synopsis:**
```bash
aws cleanroomsml delete-configured-model-algorithm-association \
    --membership-identifier <value> \
    --configured-model-algorithm-association-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-model-algorithm-association-arn` | **Yes** | string | -- | Association ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 14.7 `get-configured-model-algorithm-association`

Returns details for an algorithm association.

**Synopsis:**
```bash
aws cleanroomsml get-configured-model-algorithm-association \
    --membership-identifier <value> \
    --configured-model-algorithm-association-arn <value>
```

**Output Schema:**
```json
{
    "membershipIdentifier": "string",
    "collaborationIdentifier": "string",
    "configuredModelAlgorithmAssociationArn": "string",
    "configuredModelAlgorithmArn": "string",
    "name": "string",
    "description": "string",
    "privacyConfiguration": {},
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "tags": {}
}
```

---

## 14.8 `list-configured-model-algorithm-associations`

Lists algorithm associations for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-configured-model-algorithm-associations \
    --membership-identifier <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

## 14.9-14.10 Collaboration Algorithm Associations

`get-collaboration-configured-model-algorithm-association` and `list-collaboration-configured-model-algorithm-associations` provide collaboration-level views.

**Synopsis (get):**
```bash
aws cleanroomsml get-collaboration-configured-model-algorithm-association \
    --configured-model-algorithm-association-arn <value> \
    --collaboration-identifier <value>
```

**Synopsis (list):**
```bash
aws cleanroomsml list-collaboration-configured-model-algorithm-associations \
    --collaboration-identifier <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```
