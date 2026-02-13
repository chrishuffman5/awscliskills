# Collections

### 2.1 `create-collection`

Creates a face collection for storing face metadata.

**Synopsis:**
```bash
aws rekognition create-collection \
    --collection-id <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID for the collection (1-255 chars, pattern: `[a-zA-Z0-9_.\-]+`) |
| `--tags` | No | map | -- | Key-value tags (max 200) |

**Output Schema:**
```json
{
    "StatusCode": "integer",
    "CollectionArn": "string",
    "FaceModelVersion": "string"
}
```

---

### 2.2 `delete-collection`

Deletes a face collection and all stored face metadata.

**Synopsis:**
```bash
aws rekognition delete-collection \
    --collection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection to delete |

**Output Schema:**
```json
{
    "StatusCode": "integer"
}
```

---

### 2.3 `describe-collection`

Describes a face collection including face count and model version.

**Synopsis:**
```bash
aws rekognition describe-collection \
    --collection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection |

**Output Schema:**
```json
{
    "FaceCount": "long",
    "FaceModelVersion": "string",
    "CollectionARN": "string",
    "CreationTimestamp": "timestamp",
    "UserCount": "long"
}
```

---

### 2.4 `list-collections`

Lists available face collections. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-collections \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "CollectionIds": ["string"],
    "NextToken": "string",
    "FaceModelVersions": ["string"]
}
```

---

### 2.5 `index-faces`

Detects faces in an image and adds them to a collection.

**Synopsis:**
```bash
aws rekognition index-faces \
    --collection-id <value> \
    [--image <value>] \
    [--image-bytes <value>] \
    [--external-image-id <value>] \
    [--detection-attributes <value>] \
    [--max-faces <value>] \
    [--quality-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | ID of the collection to add faces to |
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--external-image-id` | No | string | -- | Identifier to assign to all detected faces (1-255 chars) |
| `--detection-attributes` | No | list(string) | `DEFAULT` | Facial attributes to return: `DEFAULT`, `ALL` |
| `--max-faces` | No | integer | -- | Maximum faces to index (min: 1, max: 100) |
| `--quality-filter` | No | string | `AUTO` | Quality filter: `NONE`, `AUTO`, `LOW`, `MEDIUM`, `HIGH` |

**Output Schema:**
```json
{
    "FaceRecords": [
        {
            "Face": {
                "FaceId": "string",
                "BoundingBox": {},
                "ImageId": "string",
                "ExternalImageId": "string",
                "Confidence": "float",
                "IndexFacesModelVersion": "string",
                "UserId": "string"
            },
            "FaceDetail": {
                "BoundingBox": {},
                "AgeRange": {},
                "Smile": {},
                "Eyeglasses": {},
                "Sunglasses": {},
                "Gender": {},
                "Beard": {},
                "Mustache": {},
                "EyesOpen": {},
                "MouthOpen": {},
                "Emotions": [],
                "Landmarks": [],
                "Pose": {},
                "Quality": {},
                "Confidence": "float",
                "FaceOccluded": {},
                "EyeDirection": {}
            }
        }
    ],
    "UnindexedFaces": [
        {
            "Reasons": ["EXCEEDS_MAX_FACES|EXTREME_POSE|LOW_BRIGHTNESS|LOW_SHARPNESS|LOW_CONFIDENCE|SMALL_BOUNDING_BOX|LOW_FACE_QUALITY"],
            "FaceDetail": {}
        }
    ],
    "FaceModelVersion": "string",
    "OrientationCorrection": "ROTATE_0|ROTATE_90|ROTATE_180|ROTATE_270"
}
```

---

### 2.6 `delete-faces`

Deletes faces from a collection.

**Synopsis:**
```bash
aws rekognition delete-faces \
    --collection-id <value> \
    --face-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection containing the faces |
| `--face-ids` | **Yes** | list(string) | -- | Face IDs to delete (1-4096) |

**Output Schema:**
```json
{
    "DeletedFaces": ["string"],
    "UnsuccessfulFaceDeletions": [
        {
            "FaceId": "string",
            "UserId": "string",
            "Reasons": ["ASSOCIATED_TO_AN_EXISTING_USER|FACE_NOT_FOUND"]
        }
    ]
}
```

---

### 2.7 `list-faces`

Lists faces in a collection. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-faces \
    --collection-id <value> \
    [--user-id <value>] \
    [--face-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection to list faces from |
| `--user-id` | No | string | -- | Filter by user ID |
| `--face-ids` | No | list(string) | -- | Filter by specific face IDs |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Faces": [
        {
            "FaceId": "string",
            "BoundingBox": {},
            "ImageId": "string",
            "ExternalImageId": "string",
            "Confidence": "float",
            "IndexFacesModelVersion": "string",
            "UserId": "string"
        }
    ],
    "NextToken": "string",
    "FaceModelVersion": "string"
}
```

---

### 2.8 `search-faces`

Searches for matching faces in a collection by face ID.

**Synopsis:**
```bash
aws rekognition search-faces \
    --collection-id <value> \
    --face-id <value> \
    [--max-faces <value>] \
    [--face-match-threshold <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection to search |
| `--face-id` | **Yes** | string | -- | Face ID to search for |
| `--max-faces` | No | integer | -- | Maximum matching faces to return (1-4096) |
| `--face-match-threshold` | No | float | 80 | Minimum match confidence (0-100) |

**Output Schema:**
```json
{
    "SearchedFaceId": "string",
    "FaceMatches": [
        {
            "Similarity": "float",
            "Face": {
                "FaceId": "string",
                "BoundingBox": {},
                "ImageId": "string",
                "ExternalImageId": "string",
                "Confidence": "float",
                "UserId": "string"
            }
        }
    ],
    "FaceModelVersion": "string"
}
```

---

### 2.9 `search-faces-by-image`

Searches for matching faces in a collection using an input image.

**Synopsis:**
```bash
aws rekognition search-faces-by-image \
    --collection-id <value> \
    [--image <value>] \
    [--image-bytes <value>] \
    [--max-faces <value>] \
    [--face-match-threshold <value>] \
    [--quality-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection to search |
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--max-faces` | No | integer | -- | Maximum matching faces (1-4096) |
| `--face-match-threshold` | No | float | 80 | Minimum match confidence (0-100) |
| `--quality-filter` | No | string | `NONE` | Quality filter: `NONE`, `AUTO`, `LOW`, `MEDIUM`, `HIGH` |

**Output Schema:**
```json
{
    "SearchedFaceBoundingBox": {},
    "SearchedFaceConfidence": "float",
    "FaceMatches": [
        {
            "Similarity": "float",
            "Face": {
                "FaceId": "string",
                "BoundingBox": {},
                "ImageId": "string",
                "ExternalImageId": "string",
                "Confidence": "float",
                "UserId": "string"
            }
        }
    ],
    "FaceModelVersion": "string"
}
```
