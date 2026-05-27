# AWS CLI v2 -- Comprehend (Natural Language Processing) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/comprehend/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `detect-dominant-language` | Real-Time | Detect the dominant language of text |
| `detect-entities` | Real-Time | Detect named entities in text |
| `detect-key-phrases` | Real-Time | Detect key noun phrases in text |
| `detect-pii-entities` | Real-Time | Detect personally identifiable information in text |
| `detect-sentiment` | Real-Time | Detect sentiment (positive/negative/neutral/mixed) |
| `detect-syntax` | Real-Time | Detect syntax tokens and parts of speech |
| `detect-targeted-sentiment` | Real-Time | Detect sentiment associated with specific entities |
| `detect-toxic-content` | Real-Time | Detect toxic content in text segments |
| `contains-pii-entities` | Real-Time | Check if text contains PII entities |
| `classify-document` | Real-Time | Classify a document using a custom classifier endpoint |
| `batch-detect-dominant-language` | Batch | Detect dominant language in multiple documents |
| `batch-detect-entities` | Batch | Detect entities in multiple documents |
| `batch-detect-key-phrases` | Batch | Detect key phrases in multiple documents |
| `batch-detect-sentiment` | Batch | Detect sentiment in multiple documents |
| `batch-detect-syntax` | Batch | Detect syntax in multiple documents |
| `batch-detect-targeted-sentiment` | Batch | Detect targeted sentiment in multiple documents |
| `start-entities-detection-job` | Entity Detection Job | Start an asynchronous entities detection job |
| `describe-entities-detection-job` | Entity Detection Job | Describe an entities detection job |
| `list-entities-detection-jobs` | Entity Detection Job | List entities detection jobs |
| `stop-entities-detection-job` | Entity Detection Job | Stop an entities detection job |
| `start-document-classification-job` | Classification Job | Start a document classification job |
| `describe-document-classification-job` | Classification Job | Describe a document classification job |
| `list-document-classification-jobs` | Classification Job | List document classification jobs |
| `start-dominant-language-detection-job` | Other Job | Start a dominant language detection job |
| `describe-dominant-language-detection-job` | Other Job | Describe a dominant language detection job |
| `list-dominant-language-detection-jobs` | Other Job | List dominant language detection jobs |
| `stop-dominant-language-detection-job` | Other Job | Stop a dominant language detection job |
| `start-key-phrases-detection-job` | Other Job | Start a key phrases detection job |
| `describe-key-phrases-detection-job` | Other Job | Describe a key phrases detection job |
| `list-key-phrases-detection-jobs` | Other Job | List key phrases detection jobs |
| `stop-key-phrases-detection-job` | Other Job | Stop a key phrases detection job |
| `start-sentiment-detection-job` | Other Job | Start a sentiment detection job |
| `describe-sentiment-detection-job` | Other Job | Describe a sentiment detection job |
| `list-sentiment-detection-jobs` | Other Job | List sentiment detection jobs |
| `stop-sentiment-detection-job` | Other Job | Stop a sentiment detection job |
| `start-targeted-sentiment-detection-job` | Other Job | Start a targeted sentiment detection job |
| `describe-targeted-sentiment-detection-job` | Other Job | Describe a targeted sentiment detection job |
| `list-targeted-sentiment-detection-jobs` | Other Job | List targeted sentiment detection jobs |
| `stop-targeted-sentiment-detection-job` | Other Job | Stop a targeted sentiment detection job |
| `start-pii-entities-detection-job` | Other Job | Start a PII entities detection job |
| `describe-pii-entities-detection-job` | Other Job | Describe a PII entities detection job |
| `list-pii-entities-detection-jobs` | Other Job | List PII entities detection jobs |
| `stop-pii-entities-detection-job` | Other Job | Stop a PII entities detection job |
| `start-events-detection-job` | Other Job | Start an events detection job |
| `describe-events-detection-job` | Other Job | Describe an events detection job |
| `list-events-detection-jobs` | Other Job | List events detection jobs |
| `stop-events-detection-job` | Other Job | Stop an events detection job |
| `start-topics-detection-job` | Other Job | Start a topics detection job |
| `describe-topics-detection-job` | Other Job | Describe a topics detection job |
| `list-topics-detection-jobs` | Other Job | List topics detection jobs |
| `create-document-classifier` | Document Classifier | Create a custom document classifier |
| `delete-document-classifier` | Document Classifier | Delete a document classifier |
| `describe-document-classifier` | Document Classifier | Describe a document classifier |
| `list-document-classifiers` | Document Classifier | List document classifiers |
| `list-document-classifier-summaries` | Document Classifier | List document classifier summaries |
| `stop-training-document-classifier` | Document Classifier | Stop training a document classifier |
| `create-entity-recognizer` | Entity Recognizer | Create a custom entity recognizer |
| `delete-entity-recognizer` | Entity Recognizer | Delete an entity recognizer |
| `describe-entity-recognizer` | Entity Recognizer | Describe an entity recognizer |
| `list-entity-recognizers` | Entity Recognizer | List entity recognizers |
| `list-entity-recognizer-summaries` | Entity Recognizer | List entity recognizer summaries |
| `stop-training-entity-recognizer` | Entity Recognizer | Stop training an entity recognizer |
| `create-endpoint` | Endpoint | Create a model endpoint for real-time inference |
| `delete-endpoint` | Endpoint | Delete an endpoint |
| `describe-endpoint` | Endpoint | Describe an endpoint |
| `list-endpoints` | Endpoint | List endpoints |
| `update-endpoint` | Endpoint | Update an endpoint |
| `create-flywheel` | Flywheel | Create a flywheel for automated retraining |
| `delete-flywheel` | Flywheel | Delete a flywheel |
| `describe-flywheel` | Flywheel | Describe a flywheel |
| `list-flywheels` | Flywheel | List flywheels |
| `update-flywheel` | Flywheel | Update a flywheel |
| `start-flywheel-iteration` | Flywheel | Start a flywheel iteration |
| `describe-flywheel-iteration` | Flywheel | Describe a flywheel iteration |
| `list-flywheel-iteration-history` | Flywheel | List flywheel iteration history |
| `create-dataset` | Dataset | Create a dataset for a flywheel |
| `describe-dataset` | Dataset | Describe a dataset |
| `list-datasets` | Dataset | List datasets for a flywheel |
| `put-resource-policy` | Resource Policy | Attach a resource-based policy to a custom model |
| `delete-resource-policy` | Resource Policy | Delete a resource-based policy |
| `describe-resource-policy` | Resource Policy | Describe a resource-based policy |
| `import-model` | Resource Policy | Import a custom model from another account |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws comprehend` commands.

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

### Supported Language Codes
| Code | Language |
|------|----------|
| `en` | English |
| `es` | Spanish |
| `fr` | French |
| `de` | German |
| `it` | Italian |
| `pt` | Portuguese |
| `ar` | Arabic |
| `hi` | Hindi |
| `ja` | Japanese |
| `ko` | Korean |
| `zh` | Chinese (Simplified) |
| `zh-TW` | Chinese (Traditional) |

### Entity Types (Built-in)
| Type | Description |
|------|-------------|
| `PERSON` | People, including fictional |
| `LOCATION` | Geographical locations |
| `ORGANIZATION` | Organizations, companies |
| `COMMERCIAL_ITEM` | Products, brands |
| `EVENT` | Named events |
| `DATE` | Dates, date ranges |
| `QUANTITY` | Numbers, quantities |
| `TITLE` | Titles of works |
| `OTHER` | Other entities |

### Job Status Values
| Status | Description |
|--------|-------------|
| `SUBMITTED` | Job has been submitted |
| `IN_PROGRESS` | Job is currently running |
| `COMPLETED` | Job completed successfully |
| `FAILED` | Job failed |
| `STOP_REQUESTED` | Stop has been requested |
| `STOPPED` | Job has been stopped |

### Model Status Values
| Status | Description |
|--------|-------------|
| `SUBMITTED` | Training submitted |
| `TRAINING` | Model is training |
| `TRAINED` | Training completed successfully |
| `TRAINED_WITH_WARNING` | Training completed with warnings |
| `DELETING` | Model is being deleted |
| `STOP_REQUESTED` | Stop has been requested |
| `STOPPED` | Training has been stopped |
| `IN_ERROR` | Training failed |
