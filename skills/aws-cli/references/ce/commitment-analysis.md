# Commitment Analysis

### 7.1 `start-commitment-purchase-analysis`

Initiates a commitment purchase analysis to estimate the cost, coverage, and utilization impact of planned Savings Plans purchases.

**Synopsis:**
```bash
aws ce start-commitment-purchase-analysis \
    --commitment-purchase-analysis-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--commitment-purchase-analysis-configuration` | **Yes** | structure | -- | Analysis configuration (Savings Plans) |

**SavingsPlansPurchaseAnalysisConfiguration Structure:**
```json
{
    "SavingsPlansPurchaseAnalysisConfiguration": {
        "AccountScope": "PAYER|LINKED",
        "AccountId": "string",
        "AnalysisType": "MAX_SAVINGS|CUSTOM_COMMITMENT",
        "SavingsPlansToAdd": [
            {
                "PaymentOption": "NO_UPFRONT|PARTIAL_UPFRONT|ALL_UPFRONT",
                "SavingsPlansType": "COMPUTE_SP|EC2_INSTANCE_SP|SAGEMAKER_SP|DATABASE_SP",
                "Region": "string",
                "InstanceFamily": "string",
                "TermInYears": "ONE_YEAR|THREE_YEARS",
                "SavingsPlansCommitment": "double",
                "OfferingId": "string"
            }
        ],
        "SavingsPlansToExclude": ["string"],
        "LookBackTimePeriod": {
            "Start": "string",
            "End": "string"
        }
    }
}
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `AnalysisType` | **Yes** | string | `MAX_SAVINGS` or `CUSTOM_COMMITMENT` |
| `SavingsPlansToAdd` | **Yes** | list | Plans to evaluate (max 1) |
| `LookBackTimePeriod` | **Yes** | structure | Historical period to analyze |
| `AccountScope` | No | string | `PAYER` or `LINKED` |
| `AccountId` | No | string | 12-digit account ID |
| `SavingsPlansToExclude` | No | list(string) | Plan IDs to exclude (max 1000) |

**Output Schema:**
```json
{
    "AnalysisId": "string",
    "AnalysisStartedTime": "string",
    "EstimatedCompletionTime": "string"
}
```

---

### 7.2 `get-commitment-purchase-analysis`

Retrieves the results of a commitment purchase analysis.

**Synopsis:**
```bash
aws ce get-commitment-purchase-analysis \
    --analysis-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analysis-id` | **Yes** | string | -- | UUID of the analysis (36 chars) |

**Output Schema:**
```json
{
    "EstimatedCompletionTime": "string",
    "AnalysisCompletionTime": "string",
    "AnalysisStartedTime": "string",
    "AnalysisId": "string",
    "AnalysisStatus": "SUCCEEDED|PROCESSING|FAILED",
    "ErrorCode": "NO_USAGE_FOUND|INTERNAL_FAILURE|INVALID_SAVINGS_PLANS",
    "AnalysisDetails": {
        "SavingsPlansPurchaseAnalysisDetails": {
            "CurrencyCode": "string",
            "LookbackPeriodInHours": "string",
            "CurrentAverageCoverage": "string",
            "CurrentAverageHourlyOnDemandSpend": "string",
            "CurrentMaximumHourlyOnDemandSpend": "string",
            "CurrentMinimumHourlyOnDemandSpend": "string",
            "CurrentOnDemandSpend": "string",
            "ExistingHourlyCommitment": "string",
            "HourlyCommitmentToPurchase": "string",
            "EstimatedAverageCoverage": "string",
            "EstimatedAverageUtilization": "string",
            "EstimatedMonthlySavingsAmount": "string",
            "EstimatedOnDemandCost": "string",
            "EstimatedOnDemandCostWithCurrentCommitment": "string",
            "EstimatedROI": "string",
            "EstimatedSPCost": "string",
            "EstimatedSavingsAmount": "string",
            "EstimatedSavingsPercentage": "string",
            "EstimatedCommitmentCost": "string",
            "LatestUsageTimestamp": "string",
            "UpfrontCost": "string",
            "AdditionalMetadata": "string",
            "MetricsOverLookbackPeriod": [
                {
                    "StartTime": "string",
                    "EstimatedOnDemandCost": "string",
                    "CurrentCoverage": "string",
                    "EstimatedCoverage": "string",
                    "EstimatedNewCommitmentUtilization": "string"
                }
            ]
        }
    },
    "CommitmentPurchaseAnalysisConfiguration": {}
}
```

---

### 7.3 `list-commitment-purchase-analyses`

Lists commitment purchase analyses. **Paginated.**

**Synopsis:**
```bash
aws ce list-commitment-purchase-analyses \
    [--analysis-status <value>] \
    [--analysis-ids <value>] \
    [--next-page-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analysis-status` | No | string | None | `SUCCEEDED`, `PROCESSING`, or `FAILED` |
| `--analysis-ids` | No | list(string) | None | Specific analysis IDs to retrieve |
| `--next-page-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |

**Output Schema:**
```json
{
    "AnalysisSummaryList": [
        {
            "EstimatedCompletionTime": "string",
            "AnalysisCompletionTime": "string",
            "AnalysisStartedTime": "string",
            "AnalysisStatus": "SUCCEEDED|PROCESSING|FAILED",
            "AnalysisId": "string",
            "CommitmentPurchaseAnalysisConfiguration": {}
        }
    ],
    "NextPageToken": "string"
}
```
