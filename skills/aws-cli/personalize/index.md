# AWS CLI v2 -- Amazon Personalize Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/personalize/ + personalize-runtime/ + personalize-events/

---

## Quick Reference — personalize

| Command | Category | Description |
|---------|----------|-------------|
| `create-dataset-group` | Dataset Group | Create a dataset group |
| `describe-dataset-group` | Dataset Group | Describe a dataset group |
| `list-dataset-groups` | Dataset Group | List all dataset groups |
| `delete-dataset-group` | Dataset Group | Delete a dataset group |
| `create-dataset` | Dataset | Create a dataset in a dataset group |
| `describe-dataset` | Dataset | Describe a dataset |
| `list-datasets` | Dataset | List datasets in a dataset group |
| `update-dataset` | Dataset | Update a dataset |
| `delete-dataset` | Dataset | Delete a dataset |
| `create-dataset-import-job` | Dataset | Create a dataset import job from S3 |
| `describe-dataset-import-job` | Dataset | Describe a dataset import job |
| `list-dataset-import-jobs` | Dataset | List dataset import jobs |
| `create-dataset-export-job` | Dataset | Create a dataset export job to S3 |
| `describe-dataset-export-job` | Dataset | Describe a dataset export job |
| `list-dataset-export-jobs` | Dataset | List dataset export jobs |
| `create-data-deletion-job` | Dataset | Create a data deletion job |
| `describe-data-deletion-job` | Dataset | Describe a data deletion job |
| `list-data-deletion-jobs` | Dataset | List data deletion jobs |
| `create-schema` | Schema | Create an Avro schema |
| `describe-schema` | Schema | Describe a schema |
| `list-schemas` | Schema | List all schemas |
| `delete-schema` | Schema | Delete a schema |
| `create-solution` | Solution | Create a solution (ML model configuration) |
| `describe-solution` | Solution | Describe a solution |
| `list-solutions` | Solution | List solutions in a dataset group |
| `update-solution` | Solution | Update a solution |
| `delete-solution` | Solution | Delete a solution |
| `create-solution-version` | Solution | Train a new solution version |
| `describe-solution-version` | Solution | Describe a solution version |
| `list-solution-versions` | Solution | List solution versions |
| `get-solution-metrics` | Solution | Get metrics for a solution version |
| `stop-solution-version-creation` | Solution | Stop training a solution version |
| `create-campaign` | Campaign | Deploy a solution version as a campaign |
| `describe-campaign` | Campaign | Describe a campaign |
| `list-campaigns` | Campaign | List campaigns for a solution |
| `update-campaign` | Campaign | Update a campaign |
| `delete-campaign` | Campaign | Delete a campaign |
| `create-recommender` | Recommender | Create a recommender (Domain dataset groups) |
| `describe-recommender` | Recommender | Describe a recommender |
| `list-recommenders` | Recommender | List recommenders |
| `update-recommender` | Recommender | Update a recommender |
| `delete-recommender` | Recommender | Delete a recommender |
| `start-recommender` | Recommender | Start a stopped recommender |
| `stop-recommender` | Recommender | Stop a running recommender |
| `create-batch-inference-job` | Batch | Create a batch inference job |
| `describe-batch-inference-job` | Batch | Describe a batch inference job |
| `list-batch-inference-jobs` | Batch | List batch inference jobs |
| `create-batch-segment-job` | Batch | Create a batch segment job |
| `describe-batch-segment-job` | Batch | Describe a batch segment job |
| `list-batch-segment-jobs` | Batch | List batch segment jobs |
| `create-event-tracker` | Event Tracker | Create an event tracker for real-time events |
| `describe-event-tracker` | Event Tracker | Describe an event tracker |
| `list-event-trackers` | Event Tracker | List event trackers |
| `delete-event-tracker` | Event Tracker | Delete an event tracker |
| `create-filter` | Filter | Create a recommendation filter |
| `describe-filter` | Filter | Describe a filter |
| `list-filters` | Filter | List filters |
| `delete-filter` | Filter | Delete a filter |
| `create-metric-attribution` | Metrics | Create metric attribution |
| `describe-metric-attribution` | Metrics | Describe metric attribution |
| `list-metric-attributions` | Metrics | List metric attributions |
| `list-metric-attribution-metrics` | Metrics | List metric attribution metrics |
| `update-metric-attribution` | Metrics | Update metric attribution |
| `delete-metric-attribution` | Metrics | Delete metric attribution |
| `describe-algorithm` | Reference | Describe an algorithm |
| `describe-feature-transformation` | Reference | Describe a feature transformation |
| `describe-recipe` | Reference | Describe a recipe |
| `list-recipes` | Reference | List available recipes |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — personalize-runtime

| Command | Category | Description |
|---------|----------|-------------|
| `get-recommendations` | Runtime | Get item recommendations for a user or related items |
| `get-personalized-ranking` | Runtime | Re-rank a list of items for a user |
| `get-action-recommendations` | Runtime | Get action recommendations for a user |

## Quick Reference — personalize-events

| Command | Category | Description |
|---------|----------|-------------|
| `put-events` | Events | Record user interaction events in real time |
| `put-items` | Events | Add or update item data in real time |
| `put-users` | Events | Add or update user data in real time |
| `put-actions` | Events | Add or update action data in real time |
| `put-action-interactions` | Events | Record action interaction events in real time |

---

## Global Options

These options are available on ALL `aws personalize`, `aws personalize-runtime`, and `aws personalize-events` commands.

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

### Resource Status Values
Most Personalize resources follow this status pattern:
| Status | Description |
|--------|-------------|
| `CREATE PENDING` | Resource creation has been requested |
| `CREATE IN_PROGRESS` | Resource is being created |
| `ACTIVE` | Resource is ready for use |
| `CREATE FAILED` | Resource creation failed |
| `DELETE PENDING` | Deletion has been requested |
| `DELETE IN_PROGRESS` | Resource is being deleted |

### Dataset Types
| Type | Description |
|------|-------------|
| `Interactions` | User-item interaction data (required) |
| `Items` | Item metadata |
| `Users` | User metadata |
| `Actions` | Action metadata |
| `Action_Interactions` | User-action interaction data |

### Domain Dataset Group Domains
| Domain | Description |
|--------|-------------|
| `ECOMMERCE` | E-commerce recommendations |
| `VIDEO_ON_DEMAND` | Video streaming recommendations |

### Common Recipes
| Recipe ARN | Use Case |
|------------|----------|
| `arn:aws:personalize:::recipe/aws-user-personalization` | Personalized recommendations for users |
| `arn:aws:personalize:::recipe/aws-similar-items` | Related items recommendations |
| `arn:aws:personalize:::recipe/aws-personalized-ranking` | Re-rank items for a user |
| `arn:aws:personalize:::recipe/aws-trending-now` | Currently trending items |
| `arn:aws:personalize:::recipe/aws-popularity-count` | Most popular items |
