# AWS CLI v2 -- ECR (Elastic Container Registry) Command Reference Index

> Based on AWS CLI v2.33.19 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/ecr/

---

## Table of Contents

1. [Repository Management](#1-repository-management)
2. [Image Management](#2-image-management)
3. [Image Scanning](#3-image-scanning)
4. [Lifecycle Policies](#4-lifecycle-policies)
5. [Authentication](#5-authentication)
6. [Registry Management](#6-registry-management)
7. [Tags](#7-tags)
8. [Global Options Reference](#8-global-options-reference)

---


---

## All ECR Subcommands (Quick Reference)

| Command | Category | Description |
|---------|----------|-------------|
| `batch-check-layer-availability` | Image | Check availability of image layers |
| `batch-delete-image` | Image | Delete multiple images |
| `batch-get-image` | Image | Retrieve multiple images |
| `batch-get-repository-scanning-configuration` | Scanning | Get scanning config for repositories |
| `complete-layer-upload` | Layer | Complete a layer upload |
| `create-pull-through-cache-rule` | Registry | Create cache rule |
| `create-repository` | Repository | Create a new repository |
| `create-repository-creation-template` | Repository | Create automatic repository templates |
| `delete-lifecycle-policy` | Lifecycle | Remove lifecycle policy |
| `delete-pull-through-cache-rule` | Registry | Delete cache rule |
| `delete-registry-policy` | Registry | Remove registry policy |
| `delete-repository` | Repository | Delete a repository |
| `delete-repository-policy` | Repository | Remove repository policy |
| `delete-signing-configuration` | Signing | Remove signing config |
| `deregister-pull-time-update-exclusion` | Registry | Remove exclusion |
| `describe-image-replication-status` | Image | Check image replication status |
| `describe-image-scan-findings` | Scanning | Get image scan vulnerability findings |
| `describe-image-signing-status` | Signing | Check image signing status |
| `describe-images` | Image | Describe image properties |
| `describe-pull-through-cache-rules` | Registry | List cache rules |
| `describe-registry` | Registry | Get registry settings |
| `describe-repositories` | Repository | Describe repositories |
| `describe-repository-creation-templates` | Repository | List templates |
| `get-account-setting` | Account | Get account settings |
| `get-authorization-token` | Auth | Get Docker login credentials |
| `get-download-url-for-layer` | Layer | Get presigned download URL |
| `get-lifecycle-policy` | Lifecycle | Retrieve lifecycle policy |
| `get-lifecycle-policy-preview` | Lifecycle | Preview lifecycle policy effects |
| `get-login-password` | Auth | Get Docker login password |
| `get-registry-policy` | Registry | Retrieve registry policy |
| `get-registry-scanning-configuration` | Registry | Get registry-level scanning config |
| `get-repository-policy` | Repository | Get repository access policy |
| `get-signing-configuration` | Signing | Get signing config |
| `initiate-layer-upload` | Layer | Initiate a layer upload |
| `list-image-referrers` | Image | List image referrers |
| `list-images` | Image | List repository images |
| `list-pull-time-update-exclusions` | Registry | List exclusions |
| `list-tags-for-resource` | Tags | List resource tags |
| `put-account-setting` | Account | Set account settings |
| `put-image` | Image | Push an image to a repository |
| `put-image-scanning-configuration` | Scanning | Set scanning configuration |
| `put-image-tag-mutability` | Repository | Configure image tag mutability |
| `put-lifecycle-policy` | Lifecycle | Set lifecycle policy |
| `put-registry-policy` | Registry | Set registry policy |
| `put-registry-scanning-configuration` | Registry | Set registry scanning config |
| `put-replication-configuration` | Registry | Configure cross-region replication |
| `put-signing-configuration` | Signing | Set signing config |
| `register-pull-time-update-exclusion` | Registry | Exclude image from updates |
| `set-repository-policy` | Repository | Set repository access policy |
| `start-image-scan` | Scanning | Initiate image vulnerability scan |
| `start-lifecycle-policy-preview` | Lifecycle | Start lifecycle preview |
| `tag-resource` | Tags | Add tags to resources |
| `untag-resource` | Tags | Remove tags from resources |
| `update-image-storage-class` | Image | Modify image storage class |
| `update-pull-through-cache-rule` | Registry | Modify cache rule |
| `update-repository-creation-template` | Repository | Modify template |
| `upload-layer-part` | Layer | Upload a layer part |
| `validate-pull-through-cache-rule` | Registry | Validate cache rule |

---


---

## 8. Global Options Reference

These options are available on ALL `aws ecr` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
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


---

## Common Patterns

### Repository Name Constraints
- **Length:** 2-256 characters
- **Pattern:** `(?:[a-z0-9]+(?:[._-][a-z0-9]+)*/)*[a-z0-9]+(?:[._-][a-z0-9]+)*`
- Must start with a lowercase letter
- Allowed characters: lowercase letters, numbers, hyphens, underscores, forward slashes, periods
- Supports namespace prefixes: `project-a/my-repo`

### Registry ID Constraints
- **Pattern:** `[0-9]{12}` (12-digit AWS account ID)
- Optional on all commands; defaults to the caller's AWS account

### Image ID Structure
Used by `batch-get-image`, `batch-delete-image`, `describe-images`, `start-image-scan`, `describe-image-scan-findings`:
```json
{
    "imageDigest": "sha256:<64-hex-chars>",
    "imageTag": "string (1-300 chars)"
}
```
At least one of `imageDigest` or `imageTag` must be provided.

### Failure Codes (Image Operations)
| Code | Description |
|------|-------------|
| `InvalidImageDigest` | The specified image digest is invalid |
| `InvalidImageTag` | The specified image tag is invalid |
| `ImageTagDoesNotMatchDigest` | The tag does not match the digest |
| `ImageNotFound` | The image was not found |
| `MissingDigestAndTag` | Neither digest nor tag was provided |
| `ImageReferencedByManifestList` | Image is referenced by a manifest list |
| `KmsError` | KMS encryption error |
| `UpstreamAccessDenied` | Access denied to upstream registry |
| `UpstreamTooManyRequests` | Rate limited by upstream registry |
| `UpstreamUnavailable` | Upstream registry is unavailable |
| `ImageInaccessible` | Image is not accessible |

### Image Scan Status Values
| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Scan is currently running |
| `COMPLETE` | Scan completed successfully |
| `FAILED` | Scan failed |
| `UNSUPPORTED_IMAGE` | Image type is not supported for scanning |
| `ACTIVE` | Enhanced scanning is active |
| `PENDING` | Scan is queued |
| `SCAN_ELIGIBILITY_EXPIRED` | Scan eligibility has expired |
| `FINDINGS_UNAVAILABLE` | Findings are not available |
| `LIMIT_EXCEEDED` | Scan limit exceeded |
| `IMAGE_ARCHIVED` | Image has been archived |
