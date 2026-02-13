# Algorithms

## 1. `create-algorithm`

Creates a custom algorithm resource for use in training jobs and hyperparameter tuning.

**Synopsis:**
```bash
aws sagemaker create-algorithm \
    --algorithm-name <value> \
    --training-specification <value> \
    [--algorithm-description <value>] \
    [--inference-specification <value>] \
    [--validation-specification <value>] \
    [--certify-for-marketplace | --no-certify-for-marketplace] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--algorithm-name` | **Yes** | string | -- | Algorithm name (1-63 chars) |
| `--training-specification` | **Yes** | structure | -- | Training image, instance types, hyperparameters, input channels, metrics |
| `--algorithm-description` | No | string | -- | Description |
| `--inference-specification` | No | structure | -- | Inference image and instance types |
| `--validation-specification` | No | structure | -- | Validation profiles and IAM role |
| `--certify-for-marketplace` | No | boolean | false | Certify for AWS Marketplace |
| `--tags` | No | list | -- | Key-value tags |

**Training Specification:**
```json
{
    "TrainingImage": "string",
    "TrainingImageDigest": "string",
    "SupportedHyperParameters": [
        {
            "Name": "string",
            "Description": "string",
            "Type": "Integer|Continuous|Categorical|FreeText",
            "Range": {
                "IntegerParameterRangeSpecification": {"MinValue": "string", "MaxValue": "string"},
                "ContinuousParameterRangeSpecification": {"MinValue": "string", "MaxValue": "string"},
                "CategoricalParameterRangeSpecification": {"Values": ["string"]}
            },
            "IsTunable": "boolean",
            "IsRequired": "boolean",
            "DefaultValue": "string"
        }
    ],
    "SupportedTrainingInstanceTypes": ["ml.m5.xlarge", "ml.p3.2xlarge", "..."],
    "SupportsDistributedTraining": "boolean",
    "MetricDefinitions": [{"Name": "string", "Regex": "string"}],
    "TrainingChannels": [
        {
            "Name": "string",
            "Description": "string",
            "IsRequired": "boolean",
            "SupportedContentTypes": ["string"],
            "SupportedCompressionTypes": ["None", "Gzip"],
            "SupportedInputModes": ["Pipe", "File"]
        }
    ],
    "SupportedTuningJobObjectiveMetrics": [{"Type": "Maximize|Minimize", "MetricName": "string"}]
}
```

**Output Schema:**
```json
{
    "AlgorithmArn": "string"
}
```

---

## 2. `describe-algorithm`

Returns details about an algorithm.

```bash
aws sagemaker describe-algorithm --algorithm-name <value>
```

**Output Schema:**
```json
{
    "AlgorithmName": "string",
    "AlgorithmArn": "string",
    "AlgorithmDescription": "string",
    "CreationTime": "timestamp",
    "TrainingSpecification": {...},
    "InferenceSpecification": {...},
    "ValidationSpecification": {...},
    "AlgorithmStatus": "Pending|InProgress|Completed|Failed|Deleting",
    "AlgorithmStatusDetails": {
        "ValidationStatuses": [{"Name": "string", "Status": "NotStarted|InProgress|Completed|Failed", "FailureReason": "string"}],
        "ImageScanStatuses": [...]
    },
    "ProductId": "string",
    "CertifyForMarketplace": "boolean"
}
```

---

## 3. `list-algorithms`

Lists algorithms. **Paginated operation.**

```bash
aws sagemaker list-algorithms \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-contains` | No | string | -- | Filter by name substring |
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

---

## 4. `delete-algorithm`

Deletes an algorithm.

```bash
aws sagemaker delete-algorithm --algorithm-name <value>
```

**Output:** None
