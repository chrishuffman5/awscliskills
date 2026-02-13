# Users

### 3.1 `create-user`

Creates a new user within a collection. A user represents a single individual who can have multiple face IDs associated.

**Synopsis:**
```bash
aws rekognition create-user \
    --collection-id <value> \
    --user-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection (1-255 chars) |
| `--user-id` | **Yes** | string | -- | ID for the user (1-128 chars, pattern: `[a-zA-Z0-9_.\-:]+`) |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |

**Output:** None (HTTP 200 on success)

---

### 3.2 `delete-user`

Deletes a user from a collection. Associated faces are disassociated but not deleted.

**Synopsis:**
```bash
aws rekognition delete-user \
    --collection-id <value> \
    --user-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection |
| `--user-id` | **Yes** | string | -- | ID of the user to delete |
| `--client-request-token` | No | string | auto | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 3.3 `list-users`

Lists users in a collection. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-users \
    --collection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Users": [
        {
            "UserId": "string",
            "UserStatus": "ACTIVE|UPDATING|CREATING|CREATED"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `associate-faces`

Associates one or more faces with a user.

**Synopsis:**
```bash
aws rekognition associate-faces \
    --collection-id <value> \
    --user-id <value> \
    --face-ids <value> \
    [--user-match-threshold <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection |
| `--user-id` | **Yes** | string | -- | ID of the user |
| `--face-ids` | **Yes** | list(string) | -- | Face IDs to associate (1-100) |
| `--user-match-threshold` | No | float | 75 | Minimum similarity confidence for user match verification (0-100) |
| `--client-request-token` | No | string | auto | Idempotency token |

**Output Schema:**
```json
{
    "AssociatedFaces": [
        {
            "FaceId": "string"
        }
    ],
    "UnsuccessfulFaceAssociations": [
        {
            "FaceId": "string",
            "UserId": "string",
            "Confidence": "float",
            "Reasons": ["FACE_NOT_FOUND|ASSOCIATED_TO_A_DIFFERENT_USER|LOW_MATCH_CONFIDENCE"]
        }
    ],
    "UserStatus": "ACTIVE|UPDATING|CREATING|CREATED"
}
```

---

### 3.5 `disassociate-faces`

Removes one or more faces from a user.

**Synopsis:**
```bash
aws rekognition disassociate-faces \
    --collection-id <value> \
    --user-id <value> \
    --face-ids <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection |
| `--user-id` | **Yes** | string | -- | ID of the user |
| `--face-ids` | **Yes** | list(string) | -- | Face IDs to disassociate (1-100) |
| `--client-request-token` | No | string | auto | Idempotency token |

**Output Schema:**
```json
{
    "DisassociatedFaces": [
        {
            "FaceId": "string"
        }
    ],
    "UnsuccessfulFaceDisassociations": [
        {
            "FaceId": "string",
            "UserId": "string",
            "Reasons": ["FACE_NOT_FOUND|ASSOCIATED_TO_A_DIFFERENT_USER"]
        }
    ],
    "UserStatus": "ACTIVE|UPDATING|CREATING|CREATED"
}
```

---

### 3.6 `search-users`

Searches for matching users by user ID or face ID.

**Synopsis:**
```bash
aws rekognition search-users \
    --collection-id <value> \
    [--user-id <value>] \
    [--face-id <value>] \
    [--user-match-threshold <value>] \
    [--max-users <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection |
| `--user-id` | No* | string | -- | User ID to search for |
| `--face-id` | No* | string | -- | Face ID to search for |
| `--user-match-threshold` | No | float | 80 | Minimum match confidence (0-100) |
| `--max-users` | No | integer | -- | Maximum users to return (1-500) |

*Either `--user-id` or `--face-id` must be provided.

**Output Schema:**
```json
{
    "UserMatches": [
        {
            "Similarity": "float",
            "User": {
                "UserId": "string",
                "UserStatus": "ACTIVE|UPDATING|CREATING|CREATED"
            }
        }
    ],
    "FaceModelVersion": "string",
    "SearchedFace": {
        "FaceId": "string"
    },
    "SearchedUser": {
        "UserId": "string"
    }
}
```

---

### 3.7 `search-users-by-image`

Searches for matching users using an input image.

**Synopsis:**
```bash
aws rekognition search-users-by-image \
    --collection-id <value> \
    [--image <value>] \
    [--image-bytes <value>] \
    [--user-match-threshold <value>] \
    [--max-users <value>] \
    [--quality-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection |
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--user-match-threshold` | No | float | 80 | Minimum match confidence (0-100) |
| `--max-users` | No | integer | -- | Maximum users to return (1-500) |
| `--quality-filter` | No | string | `NONE` | Quality filter: `NONE`, `AUTO`, `LOW`, `MEDIUM`, `HIGH` |

**Output Schema:**
```json
{
    "UserMatches": [
        {
            "Similarity": "float",
            "User": {
                "UserId": "string",
                "UserStatus": "string"
            }
        }
    ],
    "FaceModelVersion": "string",
    "SearchedFace": {
        "FaceDetail": {}
    },
    "UnsearchedFaces": [
        {
            "FaceDetails": {},
            "Reasons": ["FACE_NOT_LARGEST|EXCEEDS_MAX_FACES|EXTREME_POSE|LOW_BRIGHTNESS|LOW_SHARPNESS|LOW_CONFIDENCE|SMALL_BOUNDING_BOX|LOW_FACE_QUALITY"]
        }
    ]
}
```
