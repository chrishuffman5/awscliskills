# AWS CLI v2 -- Rekognition (Image and Video Analysis) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/rekognition/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `detect-labels` | Image Analysis | Detect objects and scenes in an image |
| `detect-faces` | Image Analysis | Detect faces and facial attributes |
| `detect-text` | Image Analysis | Detect text in an image |
| `detect-moderation-labels` | Image Analysis | Detect inappropriate or offensive content |
| `detect-protective-equipment` | Image Analysis | Detect personal protective equipment |
| `compare-faces` | Image Analysis | Compare faces between two images |
| `recognize-celebrities` | Image Analysis | Recognize celebrities in an image |
| `get-celebrity-info` | Image Analysis | Get celebrity info by ID |
| `create-collection` | Collection | Create a face collection |
| `delete-collection` | Collection | Delete a face collection |
| `describe-collection` | Collection | Describe a collection |
| `list-collections` | Collection | List face collections |
| `index-faces` | Collection | Add faces to a collection |
| `delete-faces` | Collection | Delete faces from a collection |
| `list-faces` | Collection | List faces in a collection |
| `search-faces` | Collection | Search for matching faces by face ID |
| `search-faces-by-image` | Collection | Search for matching faces using an image |
| `create-user` | User | Create a user in a collection |
| `delete-user` | User | Delete a user |
| `list-users` | User | List users in a collection |
| `associate-faces` | User | Associate faces with a user |
| `disassociate-faces` | User | Disassociate faces from a user |
| `search-users` | User | Search for matching users by user ID |
| `search-users-by-image` | User | Search for matching users using an image |
| `create-face-liveness-session` | Face Liveness | Create a face liveness session |
| `get-face-liveness-session-results` | Face Liveness | Get liveness session results |
| `start-label-detection` | Video | Start label detection on stored video |
| `get-label-detection` | Video | Get label detection results |
| `start-face-detection` | Video | Start face detection on stored video |
| `get-face-detection` | Video | Get face detection results |
| `start-face-search` | Video | Start face search on stored video |
| `get-face-search` | Video | Get face search results |
| `start-celebrity-recognition` | Video | Start celebrity recognition on stored video |
| `get-celebrity-recognition` | Video | Get celebrity recognition results |
| `start-content-moderation` | Video | Start content moderation on stored video |
| `get-content-moderation` | Video | Get content moderation results |
| `start-person-tracking` | Video | Start person tracking on stored video |
| `get-person-tracking` | Video | Get person tracking results |
| `start-segment-detection` | Video | Start segment detection on stored video |
| `get-segment-detection` | Video | Get segment detection results |
| `start-text-detection` | Video | Start text detection on stored video |
| `get-text-detection` | Video | Get text detection results |
| `start-media-analysis-job` | Media Analysis | Start a media analysis job |
| `get-media-analysis-job` | Media Analysis | Get media analysis job details |
| `list-media-analysis-jobs` | Media Analysis | List media analysis jobs |
| `create-stream-processor` | Stream Processor | Create a streaming video processor |
| `delete-stream-processor` | Stream Processor | Delete a stream processor |
| `describe-stream-processor` | Stream Processor | Describe a stream processor |
| `list-stream-processors` | Stream Processor | List stream processors |
| `start-stream-processor` | Stream Processor | Start a stream processor |
| `stop-stream-processor` | Stream Processor | Stop a stream processor |
| `update-stream-processor` | Stream Processor | Update a stream processor |
| `create-project` | Project | Create a Custom Labels project |
| `delete-project` | Project | Delete a project |
| `describe-projects` | Project | Describe projects |
| `create-project-version` | Project | Train a model version |
| `delete-project-version` | Project | Delete a model version |
| `describe-project-versions` | Project | Describe model versions |
| `copy-project-version` | Project | Copy a model version |
| `start-project-version` | Project | Start (deploy) a model version |
| `stop-project-version` | Project | Stop a model version |
| `detect-custom-labels` | Project | Detect custom labels in an image |
| `put-project-policy` | Project | Add/update project policy |
| `delete-project-policy` | Project | Delete project policy |
| `list-project-policies` | Project | List project policies |
| `create-dataset` | Dataset | Create a dataset for a project |
| `delete-dataset` | Dataset | Delete a dataset |
| `describe-dataset` | Dataset | Describe a dataset |
| `list-dataset-entries` | Dataset | List dataset entries |
| `list-dataset-labels` | Dataset | List dataset labels |
| `update-dataset-entries` | Dataset | Update dataset entries |
| `distribute-dataset-entries` | Dataset | Distribute dataset entries |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `wait` | Wait | Wait for a resource state change |

---

## Global Options

These options are available on ALL `aws rekognition` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Image Input
Images can be provided as S3 objects or local files:
```bash
# S3 object
--image '{"S3Object":{"Bucket":"bucket","Name":"image.jpg"}}'

# Local file (binary)
--image-bytes fileb://image.png
```

### Video Input (Stored Video)
Videos must be stored in S3:
```bash
--video '{"S3Object":{"Bucket":"bucket","Name":"video.mp4"}}'
```

### Notification Channel (Video Jobs)
```bash
--notification-channel "SNSTopicArn=arn:aws:sns:region:account:topic,RoleArn=arn:aws:iam::account:role/role-name"
```

### BoundingBox Structure
All bounding boxes use ratios (0.0 to 1.0) relative to image dimensions:
```json
{
    "Width": "float",
    "Height": "float",
    "Left": "float",
    "Top": "float"
}
```
