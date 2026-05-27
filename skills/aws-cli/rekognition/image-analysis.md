# Image Analysis

### 1.1 `detect-labels`

Detects objects, scenes, and concepts in an image. Returns labels with confidence scores and bounding boxes.

**Synopsis:**
```bash
aws rekognition detect-labels \
    [--image <value>] \
    [--image-bytes <value>] \
    [--max-labels <value>] \
    [--min-confidence <value>] \
    [--features <value>] \
    [--settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image` | No* | structure | -- | Image as S3 object. Shorthand: `S3Object={Bucket=string,Name=string,Version=string}` |
| `--image-bytes` | No* | blob | -- | Local file content: `fileb://image.png` |
| `--max-labels` | No | integer | 1000 | Maximum labels to return (min: 0) |
| `--min-confidence` | No | float | 55 | Minimum confidence threshold (0-100) |
| `--features` | No | list(string) | -- | Analysis types: `GENERAL_LABELS`, `IMAGE_PROPERTIES` |
| `--settings` | No | structure | -- | Label and image property filters |

*Either `--image` or `--image-bytes` must be provided.

**Settings Structure:**
```json
{
    "GeneralLabels": {
        "LabelInclusionFilters": ["string"],
        "LabelExclusionFilters": ["string"],
        "LabelCategoryInclusionFilters": ["string"],
        "LabelCategoryExclusionFilters": ["string"]
    },
    "ImageProperties": {
        "MaxDominantColors": "integer (0-20, default 10)"
    }
}
```

**Output Schema:**
```json
{
    "Labels": [
        {
            "Name": "string",
            "Confidence": "float",
            "Instances": [
                {
                    "BoundingBox": {
                        "Width": "float",
                        "Height": "float",
                        "Left": "float",
                        "Top": "float"
                    },
                    "Confidence": "float",
                    "DominantColors": [
                        {
                            "Red": "integer",
                            "Blue": "integer",
                            "Green": "integer",
                            "HexCode": "string",
                            "CSSColor": "string",
                            "SimplifiedColor": "string",
                            "PixelPercent": "float"
                        }
                    ]
                }
            ],
            "Parents": [{"Name": "string"}],
            "Aliases": [{"Name": "string"}],
            "Categories": [{"Name": "string"}]
        }
    ],
    "OrientationCorrection": "ROTATE_0|ROTATE_90|ROTATE_180|ROTATE_270",
    "LabelModelVersion": "string",
    "ImageProperties": {
        "Quality": {"Brightness": "float", "Sharpness": "float", "Contrast": "float"},
        "DominantColors": [],
        "Foreground": {"Quality": {}, "DominantColors": []},
        "Background": {"Quality": {}, "DominantColors": []}
    }
}
```

---

### 1.2 `detect-faces`

Detects faces in an image and returns facial attributes (age, emotions, landmarks, pose, quality).

**Synopsis:**
```bash
aws rekognition detect-faces \
    [--image <value>] \
    [--image-bytes <value>] \
    [--attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--attributes` | No | list(string) | `DEFAULT` | Attributes to return: `DEFAULT`, `ALL`, `AGE_RANGE`, `BEARD`, `EMOTIONS`, `EYE_DIRECTION`, `EYEGLASSES`, `EYES_OPEN`, `GENDER`, `MOUTH_OPEN`, `MUSTACHE`, `FACE_OCCLUDED`, `SMILE`, `SUNGLASSES` |

**Output Schema:**
```json
{
    "FaceDetails": [
        {
            "BoundingBox": {"Width": "float", "Height": "float", "Left": "float", "Top": "float"},
            "Confidence": "float",
            "Landmarks": [{"Type": "string", "X": "float", "Y": "float"}],
            "Pose": {"Roll": "float", "Pitch": "float", "Yaw": "float"},
            "Quality": {"Brightness": "float", "Sharpness": "float"},
            "AgeRange": {"Low": "integer", "High": "integer"},
            "Smile": {"Value": "boolean", "Confidence": "float"},
            "Eyeglasses": {"Value": "boolean", "Confidence": "float"},
            "Sunglasses": {"Value": "boolean", "Confidence": "float"},
            "Gender": {"Value": "Male|Female", "Confidence": "float"},
            "Beard": {"Value": "boolean", "Confidence": "float"},
            "Mustache": {"Value": "boolean", "Confidence": "float"},
            "EyesOpen": {"Value": "boolean", "Confidence": "float"},
            "MouthOpen": {"Value": "boolean", "Confidence": "float"},
            "Emotions": [{"Type": "HAPPY|SAD|ANGRY|CONFUSED|DISGUSTED|SURPRISED|CALM|UNKNOWN|FEAR", "Confidence": "float"}],
            "FaceOccluded": {"Value": "boolean", "Confidence": "float"},
            "EyeDirection": {"Yaw": "float", "Pitch": "float", "Confidence": "float"}
        }
    ],
    "OrientationCorrection": "ROTATE_0|ROTATE_90|ROTATE_180|ROTATE_270"
}
```

---

### 1.3 `detect-text`

Detects text in an image. Returns detected lines and words with confidence scores and geometry.

**Synopsis:**
```bash
aws rekognition detect-text \
    [--image <value>] \
    [--image-bytes <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--filters` | No | structure | -- | Text detection filters (word/region filters) |

**Output Schema:**
```json
{
    "TextDetections": [
        {
            "DetectedText": "string",
            "Type": "LINE|WORD",
            "Id": "integer",
            "ParentId": "integer",
            "Confidence": "float",
            "Geometry": {
                "BoundingBox": {"Width": "float", "Height": "float", "Left": "float", "Top": "float"},
                "Polygon": [{"X": "float", "Y": "float"}]
            }
        }
    ],
    "TextModelVersion": "string"
}
```

---

### 1.4 `detect-moderation-labels`

Detects inappropriate, unwanted, or offensive content in an image.

**Synopsis:**
```bash
aws rekognition detect-moderation-labels \
    [--image <value>] \
    [--image-bytes <value>] \
    [--min-confidence <value>] \
    [--human-loop-config <value>] \
    [--project-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--min-confidence` | No | float | -- | Minimum confidence threshold (0-100) |
| `--human-loop-config` | No | structure | -- | Amazon A2I human review config |
| `--project-version` | No | string | -- | Custom moderation model version ARN |

**Output Schema:**
```json
{
    "ModerationLabels": [
        {
            "Confidence": "float",
            "Name": "string",
            "ParentName": "string",
            "TaxonomyLevel": "integer"
        }
    ],
    "ModerationModelVersion": "string",
    "HumanLoopActivationOutput": {
        "HumanLoopArn": "string",
        "HumanLoopActivationReasons": ["string"],
        "HumanLoopActivationConditionsEvaluationResults": "string"
    },
    "ContentTypes": [{"Confidence": "float", "Name": "string"}]
}
```

---

### 1.5 `detect-protective-equipment`

Detects personal protective equipment (face cover, head cover, hand cover) on persons in an image.

**Synopsis:**
```bash
aws rekognition detect-protective-equipment \
    [--image <value>] \
    [--image-bytes <value>] \
    [--summarization-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--summarization-attributes` | No | structure | -- | Required equipment types and min confidence |

**Output Schema:**
```json
{
    "ProtectiveEquipmentModelVersion": "string",
    "Persons": [
        {
            "BoundingBox": {},
            "Confidence": "float",
            "Id": "integer",
            "BodyParts": [
                {
                    "Name": "FACE|HEAD|LEFT_HAND|RIGHT_HAND",
                    "Confidence": "float",
                    "EquipmentDetections": [
                        {
                            "BoundingBox": {},
                            "Confidence": "float",
                            "Type": "FACE_COVER|HAND_COVER|HEAD_COVER",
                            "CoversBodyPart": {"Confidence": "float", "Value": "boolean"}
                        }
                    ]
                }
            ]
        }
    ],
    "Summary": {
        "PersonsWithRequiredEquipment": ["integer"],
        "PersonsWithoutRequiredEquipment": ["integer"],
        "PersonsIndeterminate": ["integer"]
    }
}
```

---

### 1.6 `compare-faces`

Compares a face in the source image with each face in the target image.

**Synopsis:**
```bash
aws rekognition compare-faces \
    --source-image <value> \
    --target-image <value> \
    [--source-image-bytes <value>] \
    [--target-image-bytes <value>] \
    [--similarity-threshold <value>] \
    [--quality-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-image` | **Yes** | structure | -- | Source image containing the face to compare |
| `--target-image` | **Yes** | structure | -- | Target image to search for matching faces |
| `--source-image-bytes` | No | blob | -- | Local source file: `fileb://source.png` |
| `--target-image-bytes` | No | blob | -- | Local target file: `fileb://target.png` |
| `--similarity-threshold` | No | float | 80 | Minimum match confidence (0-100) |
| `--quality-filter` | No | string | `NONE` | Quality filter: `NONE`, `AUTO`, `LOW`, `MEDIUM`, `HIGH` |

**Output Schema:**
```json
{
    "SourceImageFace": {
        "BoundingBox": {},
        "Confidence": "float"
    },
    "FaceMatches": [
        {
            "Similarity": "float",
            "Face": {
                "BoundingBox": {},
                "Confidence": "float",
                "Landmarks": [],
                "Pose": {},
                "Quality": {}
            }
        }
    ],
    "UnmatchedFaces": [],
    "SourceImageOrientationCorrection": "string",
    "TargetImageOrientationCorrection": "string"
}
```

---

### 1.7 `recognize-celebrities`

Recognizes celebrities in an image and returns their names and additional info URLs.

**Synopsis:**
```bash
aws rekognition recognize-celebrities \
    [--image <value>] \
    [--image-bytes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |

**Output Schema:**
```json
{
    "CelebrityFaces": [
        {
            "Urls": ["string"],
            "Name": "string",
            "Id": "string",
            "Face": {
                "BoundingBox": {},
                "Confidence": "float",
                "Landmarks": [],
                "Pose": {},
                "Quality": {}
            },
            "MatchConfidence": "float",
            "KnownGender": {"Type": "Male|Female|Nonbinary|Unlisted"}
        }
    ],
    "UnrecognizedFaces": [
        {
            "BoundingBox": {},
            "Confidence": "float",
            "Landmarks": [],
            "Pose": {},
            "Quality": {}
        }
    ],
    "OrientationCorrection": "ROTATE_0|ROTATE_90|ROTATE_180|ROTATE_270"
}
```

---

### 1.8 `get-celebrity-info`

Gets information about a recognized celebrity by their Rekognition ID.

**Synopsis:**
```bash
aws rekognition get-celebrity-info \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Rekognition celebrity ID |

**Output Schema:**
```json
{
    "Urls": ["string"],
    "Name": "string",
    "KnownGender": {
        "Type": "Male|Female|Nonbinary|Unlisted"
    }
}
```
