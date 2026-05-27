# Image Management

### 2.1 `batch-get-image`

Retrieves detailed information for images specified by `imageTag` or `imageDigest`.

**Synopsis:**
```bash
aws ecr batch-get-image \
    --repository-name <value> \
    --image-ids <value> \
    [--registry-id <value>] \
    [--accepted-media-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--image-ids` | **Yes** | list | -- | 1-100 image identifiers. Shorthand: `imageDigest=string,imageTag=string ...` |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--accepted-media-types` | No | list(string) | None | Accepted manifest media types: `application/vnd.docker.distribution.manifest.v1+json`, `application/vnd.docker.distribution.manifest.v2+json`, `application/vnd.oci.image.manifest.v1+json` |

**Image ID Structure:**
```json
{
    "imageDigest": "string",
    "imageTag": "string"
}
```

**Output Schema:**
```json
{
    "images": [
        {
            "registryId": "string",
            "repositoryName": "string",
            "imageId": {
                "imageDigest": "string",
                "imageTag": "string"
            },
            "imageManifest": "string",
            "imageManifestMediaType": "string"
        }
    ],
    "failures": [
        {
            "imageId": {
                "imageDigest": "string",
                "imageTag": "string"
            },
            "failureCode": "InvalidImageDigest|InvalidImageTag|ImageTagDoesNotMatchDigest|ImageNotFound|MissingDigestAndTag|ImageReferencedByManifestList|KmsError|UpstreamAccessDenied|UpstreamTooManyRequests|UpstreamUnavailable|ImageInaccessible",
            "failureReason": "string"
        }
    ]
}
```

---

### 2.2 `batch-delete-image`

Deletes a list of specified images within a repository.

**Synopsis:**
```bash
aws ecr batch-delete-image \
    --repository-name <value> \
    --image-ids <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--image-ids` | **Yes** | list | -- | 1-100 image identifiers. Shorthand: `imageDigest=string,imageTag=string ...` |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Output Schema:**
```json
{
    "imageIds": [
        {
            "imageDigest": "string",
            "imageTag": "string"
        }
    ],
    "failures": [
        {
            "imageId": {
                "imageDigest": "string",
                "imageTag": "string"
            },
            "failureCode": "InvalidImageDigest|InvalidImageTag|ImageTagDoesNotMatchDigest|ImageNotFound|MissingDigestAndTag|ImageReferencedByManifestList|KmsError|UpstreamAccessDenied|UpstreamTooManyRequests|UpstreamUnavailable|ImageInaccessible",
            "failureReason": "string"
        }
    ]
}
```

---

### 2.3 `describe-images`

Returns metadata about images in a repository. **Paginated operation.**

**Synopsis:**
```bash
aws ecr describe-images \
    --repository-name <value> \
    [--registry-id <value>] \
    [--image-ids <value>] \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--image-ids` | No | list | all images | 1-100 image identifiers to describe |
| `--filter` | No | structure | None | `tagStatus`: `TAGGED\|UNTAGGED\|ANY`; `imageStatus`: `ACTIVE\|ARCHIVED\|ACTIVATING\|ANY` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "imageDetails": [
        {
            "registryId": "string",
            "repositoryName": "string",
            "imageDigest": "string",
            "imageTags": ["string"],
            "imageSizeInBytes": "long",
            "imagePushedAt": "timestamp",
            "imageScanStatus": {
                "status": "IN_PROGRESS|COMPLETE|FAILED|UNSUPPORTED_IMAGE|ACTIVE|PENDING|SCAN_ELIGIBILITY_EXPIRED|FINDINGS_UNAVAILABLE|LIMIT_EXCEEDED|IMAGE_ARCHIVED",
                "description": "string"
            },
            "imageScanFindingsSummary": {
                "imageScanCompletedAt": "timestamp",
                "vulnerabilitySourceUpdatedAt": "timestamp",
                "findingSeverityCounts": {
                    "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL|UNDEFINED": "integer"
                }
            },
            "imageManifestMediaType": "string",
            "artifactMediaType": "string",
            "lastRecordedPullTime": "timestamp",
            "subjectManifestDigest": "string",
            "imageStatus": "ACTIVE|ARCHIVED|ACTIVATING",
            "lastArchivedAt": "timestamp",
            "lastActivatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

> **Note:** `imageScanFindingsSummary` and `imageScanStatus` are deprecated; use `describe-image-scan-findings` instead.

---

### 2.4 `list-images`

Lists all image IDs for a repository. **Paginated operation.**

**Synopsis:**
```bash
aws ecr list-images \
    --repository-name <value> \
    [--registry-id <value>] \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--filter` | No | structure | None | `tagStatus`: `TAGGED\|UNTAGGED\|ANY`; `imageStatus`: `ACTIVE\|ARCHIVED\|ACTIVATING\|ANY` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "imageIds": [
        {
            "imageDigest": "string",
            "imageTag": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `put-image`

Creates or updates the image manifest and tags associated with an image.

> **Note:** This is primarily used by the ECR proxy. For most use cases, use the `docker` CLI instead.

**Synopsis:**
```bash
aws ecr put-image \
    --repository-name <value> \
    --image-manifest <value> \
    [--registry-id <value>] \
    [--image-manifest-media-type <value>] \
    [--image-tag <value>] \
    [--image-digest <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--image-manifest` | **Yes** | string | -- | Image manifest JSON (1-4194304 bytes) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--image-manifest-media-type` | No | string | None | Media type of manifest (required if manifest lacks `mediaType` field) |
| `--image-tag` | No | string | None | Tag to associate (1-300 chars) |
| `--image-digest` | No | string | None | Image digest of the manifest |

**Output Schema:**
```json
{
    "image": {
        "registryId": "string",
        "repositoryName": "string",
        "imageId": {
            "imageDigest": "string",
            "imageTag": "string"
        },
        "imageManifest": "string",
        "imageManifestMediaType": "string"
    }
}
```

---

### 2.6 `batch-check-layer-availability`

Checks the availability of one or more image layers in a repository.

**Synopsis:**
```bash
aws ecr batch-check-layer-availability \
    --repository-name <value> \
    --layer-digests <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--layer-digests` | **Yes** | list(string) | -- | 1-100 layer digests (each 0-1000 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Output Schema:**
```json
{
    "layers": [
        {
            "layerDigest": "string",
            "layerAvailability": "AVAILABLE|UNAVAILABLE|ARCHIVED",
            "layerSize": "long",
            "mediaType": "string"
        }
    ],
    "failures": [
        {
            "layerDigest": "string",
            "failureCode": "InvalidLayerDigest|MissingLayerDigest",
            "failureReason": "string"
        }
    ]
}
```

---

