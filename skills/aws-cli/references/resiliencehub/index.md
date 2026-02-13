# AWS CLI v2 -- Resilience Hub Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/resiliencehub/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-app` | App | Create a Resilience Hub application |
| `delete-app` | App | Delete an application |
| `describe-app` | App | Describe an application |
| `list-apps` | App | List applications (paginated) |
| `update-app` | App | Update an application |
| `publish-app-version` | App | Publish an app version |
| `describe-app-version` | App | Describe an app version |
| `list-app-versions` | App | List app versions (paginated) |
| `update-app-version` | App | Update an app version |
| `create-app-version-app-component` | App Component | Create an app component in a version |
| `delete-app-version-app-component` | App Component | Delete an app component |
| `describe-app-version-app-component` | App Component | Describe an app component |
| `list-app-version-app-components` | App Component | List app components (paginated) |
| `update-app-version-app-component` | App Component | Update an app component |
| `create-app-version-resource` | App Resource | Create a resource in an app version |
| `delete-app-version-resource` | App Resource | Delete a resource from an app version |
| `describe-app-version-resource` | App Resource | Describe a resource in an app version |
| `list-app-version-resources` | App Resource | List resources in an app version (paginated) |
| `update-app-version-resource` | App Resource | Update a resource in an app version |
| `add-draft-app-version-resource-mappings` | App Resource | Add resource mappings to draft version |
| `remove-draft-app-version-resource-mappings` | App Resource | Remove resource mappings from draft version |
| `list-app-version-resource-mappings` | App Resource | List resource mappings (paginated) |
| `import-resources-to-draft-app-version` | App Resource | Import resources to draft version |
| `describe-draft-app-version-resources-import-status` | App Resource | Check draft resources import status |
| `describe-app-version-resources-resolution-status` | App Resource | Check resource resolution status |
| `resolve-app-version-resources` | App Resource | Resolve app version resources |
| `describe-app-version-template` | App Resource | Describe app version template |
| `put-draft-app-version-template` | App Resource | Put draft app version template |
| `list-app-input-sources` | App Resource | List app input sources (paginated) |
| `delete-app-input-source` | App Resource | Delete app input source |
| `list-unsupported-app-version-resources` | App Resource | List unsupported resources (paginated) |
| `start-app-assessment` | Assessment | Start an app assessment |
| `delete-app-assessment` | Assessment | Delete an app assessment |
| `describe-app-assessment` | Assessment | Describe an app assessment |
| `list-app-assessments` | Assessment | List app assessments (paginated) |
| `list-app-assessment-compliance-drifts` | Assessment | List compliance drifts (paginated) |
| `list-app-assessment-resource-drifts` | Assessment | List resource drifts (paginated) |
| `list-alarm-recommendations` | Recommendation | List alarm recommendations (paginated) |
| `list-sop-recommendations` | Recommendation | List SOP recommendations (paginated) |
| `list-test-recommendations` | Recommendation | List test recommendations (paginated) |
| `list-app-component-compliances` | Recommendation | List component compliances (paginated) |
| `list-app-component-recommendations` | Recommendation | List component recommendations (paginated) |
| `batch-update-recommendation-status` | Recommendation | Batch update recommendation status |
| `create-recommendation-template` | Recommendation | Create a recommendation template |
| `delete-recommendation-template` | Recommendation | Delete a recommendation template |
| `list-recommendation-templates` | Recommendation | List recommendation templates (paginated) |
| `create-resiliency-policy` | Resiliency Policy | Create a resiliency policy |
| `delete-resiliency-policy` | Resiliency Policy | Delete a resiliency policy |
| `describe-resiliency-policy` | Resiliency Policy | Describe a resiliency policy |
| `list-resiliency-policies` | Resiliency Policy | List resiliency policies (paginated) |
| `update-resiliency-policy` | Resiliency Policy | Update a resiliency policy |
| `list-suggested-resiliency-policies` | Resiliency Policy | List suggested policies (paginated) |
| `start-resource-grouping-recommendation-task` | Resource Grouping | Start resource grouping task |
| `describe-resource-grouping-recommendation-task` | Resource Grouping | Describe resource grouping task |
| `list-resource-grouping-recommendations` | Resource Grouping | List resource grouping recommendations (paginated) |
| `accept-resource-grouping-recommendations` | Resource Grouping | Accept resource grouping recommendations |
| `reject-resource-grouping-recommendations` | Resource Grouping | Reject resource grouping recommendations |
| `start-metrics-export` | Metrics | Start metrics export |
| `describe-metrics-export` | Metrics | Describe metrics export |
| `list-metrics` | Metrics | List metrics (paginated) |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags on a resource |

---

## Global Options

These options are available on ALL `aws resiliencehub` commands.

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

## Common Patterns

### Compliance Statuses
| Status | Description |
|--------|-------------|
| `PolicyBreached` | App does not meet resiliency policy targets |
| `PolicyMet` | App meets resiliency policy targets |
| `NotAssessed` | App has not been assessed |
| `ChangesDetected` | Changes detected since last assessment |
| `NotApplicable` | No applicable policy |
| `MissingPolicy` | No resiliency policy assigned |

### Drift Statuses
| Status | Description |
|--------|-------------|
| `NotChecked` | Drift has not been checked |
| `NotDetected` | No drift detected |
| `Detected` | Drift detected |

### Assessment Statuses
| Status | Description |
|--------|-------------|
| `Pending` | Assessment is pending |
| `InProgress` | Assessment is running |
| `Failed` | Assessment failed |
| `Success` | Assessment completed successfully |

### Resiliency Policy Tiers
| Tier | Description |
|------|-------------|
| `MissionCritical` | Mission-critical applications |
| `Critical` | Critical applications |
| `Important` | Important applications |
| `CoreServices` | Core service applications |
| `NonCritical` | Non-critical applications |
| `NotApplicable` | Tier not applicable |

### Disruption Types
Policy objects use these keys for RTO/RPO targets:
- `Software` — Software-level disruption
- `Hardware` — Hardware-level disruption
- `AZ` — Availability Zone disruption
- `Region` — Regional disruption

### Permission Model Types
| Type | Description |
|------|-------------|
| `RoleBased` | Uses IAM roles for cross-account access |
| `LegacyIAMUser` | Uses legacy IAM user credentials |
