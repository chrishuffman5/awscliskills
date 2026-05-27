# AWS CLI v2 -- Comprehend Medical Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/comprehendmedical/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `detect-entities-v2` | Real-Time | Detect medical entities in clinical text |
| `detect-phi` | Real-Time | Detect protected health information (PHI) |
| `infer-icd10-cm` | Real-Time | Infer ICD-10-CM diagnosis codes |
| `infer-rx-norm` | Real-Time | Infer RxNorm medication codes |
| `infer-snomedct` | Real-Time | Infer SNOMED CT medical codes |
| `start-entities-detection-v2-job` | Entity Detection | Start async entity detection job |
| `describe-entities-detection-v2-job` | Entity Detection | Get entity detection job details |
| `list-entities-detection-v2-jobs` | Entity Detection | List entity detection jobs |
| `stop-entities-detection-v2-job` | Entity Detection | Stop an entity detection job |
| `start-phi-detection-job` | PHI Detection | Start async PHI detection job |
| `describe-phi-detection-job` | PHI Detection | Get PHI detection job details |
| `list-phi-detection-jobs` | PHI Detection | List PHI detection jobs |
| `stop-phi-detection-job` | PHI Detection | Stop a PHI detection job |
| `start-icd10-cm-inference-job` | Medical Codes | Start async ICD-10-CM inference job |
| `describe-icd10-cm-inference-job` | Medical Codes | Get ICD-10-CM job details |
| `list-icd10-cm-inference-jobs` | Medical Codes | List ICD-10-CM inference jobs |
| `stop-icd10-cm-inference-job` | Medical Codes | Stop an ICD-10-CM inference job |
| `start-rx-norm-inference-job` | Medical Codes | Start async RxNorm inference job |
| `describe-rx-norm-inference-job` | Medical Codes | Get RxNorm job details |
| `list-rx-norm-inference-jobs` | Medical Codes | List RxNorm inference jobs |
| `stop-rx-norm-inference-job` | Medical Codes | Stop an RxNorm inference job |
| `start-snomedct-inference-job` | Medical Codes | Start async SNOMED CT inference job |
| `describe-snomedct-inference-job` | Medical Codes | Get SNOMED CT job details |
| `list-snomedct-inference-jobs` | Medical Codes | List SNOMED CT inference jobs |
| `stop-snomedct-inference-job` | Medical Codes | Stop a SNOMED CT inference job |

---

## Global Options

These options are available on ALL `aws comprehendmedical` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### Entity Categories
| Category | Description |
|----------|-------------|
| `MEDICATION` | Medications, dosages, routes, frequencies |
| `MEDICAL_CONDITION` | Diagnoses, signs, symptoms |
| `PROTECTED_HEALTH_INFORMATION` | PHI (names, dates, addresses, etc.) |
| `TEST_TREATMENT_PROCEDURE` | Tests, treatments, procedures |
| `ANATOMY` | Body parts, organ systems |
| `TIME_EXPRESSION` | Time-related expressions |
| `BEHAVIORAL_ENVIRONMENTAL_SOCIAL` | Lifestyle and social factors |

### Entity Traits
| Trait | Description |
|-------|-------------|
| `SIGN` | Objective clinical finding |
| `SYMPTOM` | Subjective patient report |
| `DIAGNOSIS` | Confirmed diagnosis |
| `NEGATION` | Entity is negated |
| `PERTAINS_TO_FAMILY` | Pertains to family history |
| `HYPOTHETICAL` | Hypothetical or conditional |
| `LOW_CONFIDENCE` | Low confidence detection |
| `PAST_HISTORY` | Past medical history |
| `FUTURE` | Future event or plan |

### Batch Job Status Values
| Status | Description |
|--------|-------------|
| `SUBMITTED` | Job has been submitted |
| `IN_PROGRESS` | Job is processing |
| `COMPLETED` | Job completed successfully |
| `PARTIAL_SUCCESS` | Job completed with some failures |
| `FAILED` | Job failed |
| `STOP_REQUESTED` | Stop has been requested |
| `STOPPED` | Job has been stopped |

### Text Limits
| Operation | Max Characters |
|-----------|---------------|
| `detect-entities-v2` | 20,000 |
| `detect-phi` | 20,000 |
| `infer-icd10-cm` | 10,000 |
| `infer-rx-norm` | 10,000 |
| `infer-snomedct` | 10,000 |
