# Amazon Forecast CLI Reference

Amazon Forecast is a time-series forecasting service that uses machine learning to generate accurate forecasts from historical time-series data. It supports multiple domains (retail, inventory, workforce, web traffic, EC2 capacity, metrics) and provides AutoPredictor for automated model selection.

**Note:** Amazon Forecast is no longer available to new customers as of June 2024. Existing customers can continue to use the service.

## Common Workflows

### Create a Dataset and Import Data

```bash
# Create a dataset
aws forecast create-dataset \
    --dataset-name "retail_demand" \
    --domain RETAIL \
    --dataset-type TARGET_TIME_SERIES \
    --data-frequency "1D" \
    --schema 'Attributes=[{AttributeName=item_id,AttributeType=string},{AttributeName=timestamp,AttributeType=timestamp},{AttributeName=demand,AttributeType=float}]'

# Create a dataset group
aws forecast create-dataset-group \
    --dataset-group-name "retail_group" \
    --domain RETAIL \
    --dataset-arns "arn:aws:forecast:us-east-1:123456789012:dataset/retail_demand"

# Import data from S3
aws forecast create-dataset-import-job \
    --dataset-import-job-name "import_20240101" \
    --dataset-arn "arn:aws:forecast:us-east-1:123456789012:dataset/retail_demand" \
    --data-source S3Config={Path=s3://my-bucket/data/,RoleArn=arn:aws:iam::123456789012:role/ForecastRole} \
    --timestamp-format "yyyy-MM-dd"
```

### Train a Predictor and Generate Forecast

```bash
# Create an AutoPredictor
aws forecast create-auto-predictor \
    --predictor-name "retail_predictor" \
    --forecast-horizon 30 \
    --forecast-frequency "1D" \
    --data-config '{"DatasetGroupArn":"arn:aws:forecast:us-east-1:123456789012:dataset-group/retail_group"}' \
    --optimization-metric WAPE

# Check accuracy metrics
aws forecast get-accuracy-metrics \
    --predictor-arn "arn:aws:forecast:us-east-1:123456789012:predictor/retail_predictor"

# Create a forecast
aws forecast create-forecast \
    --forecast-name "retail_forecast_q1" \
    --predictor-arn "arn:aws:forecast:us-east-1:123456789012:predictor/retail_predictor" \
    --forecast-types "0.10" "0.50" "0.90"

# Query the forecast
aws forecastquery query-forecast \
    --forecast-arn "arn:aws:forecast:us-east-1:123456789012:forecast/retail_forecast_q1" \
    --filters '{"item_id":"product_123"}'

# Export forecast to S3
aws forecast create-forecast-export-job \
    --forecast-export-job-name "export_q1" \
    --forecast-arn "arn:aws:forecast:us-east-1:123456789012:forecast/retail_forecast_q1" \
    --destination S3Config={Path=s3://my-bucket/output/,RoleArn=arn:aws:iam::123456789012:role/ForecastRole}
```

### What-If Analysis

```bash
# Create a what-if analysis
aws forecast create-what-if-analysis \
    --what-if-analysis-name "price_increase" \
    --forecast-arn "arn:aws:forecast:us-east-1:123456789012:forecast/retail_forecast_q1"

# Create a what-if forecast with transformations
aws forecast create-what-if-forecast \
    --what-if-forecast-name "price_up_10pct" \
    --what-if-analysis-arn "arn:aws:forecast:us-east-1:123456789012:what-if-analysis/price_increase" \
    --time-series-transformations '[{"Action":{"AttributeName":"price","Operation":"MULTIPLY","Value":1.10}}]'

# Query the what-if forecast
aws forecastquery query-what-if-forecast \
    --what-if-forecast-arn "arn:aws:forecast:us-east-1:123456789012:what-if-forecast/price_up_10pct" \
    --filters '{"item_id":"product_123"}'
```

### Monitoring and Explainability

```bash
# Create a monitor for predictor drift
aws forecast create-monitor \
    --monitor-name "retail_monitor" \
    --resource-arn "arn:aws:forecast:us-east-1:123456789012:predictor/retail_predictor"

# Create explainability
aws forecast create-explainability \
    --explainability-name "retail_explain" \
    --resource-arn "arn:aws:forecast:us-east-1:123456789012:predictor/retail_predictor" \
    --explainability-config TimeSeriesGranularity=ALL,TimePointGranularity=ALL

# Export explainability results
aws forecast create-explainability-export \
    --explainability-export-name "explain_export" \
    --explainability-arn "arn:aws:forecast:us-east-1:123456789012:explainability/retail_explain" \
    --destination S3Config={Path=s3://my-bucket/explain/,RoleArn=arn:aws:iam::123456789012:role/ForecastRole}
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Datasets | [`datasets.md`](datasets.md) | `create-dataset`, `describe-dataset`, `list-datasets`, `delete-dataset`, `create-dataset-group`, `describe-dataset-group`, `list-dataset-groups`, `update-dataset-group`, `delete-dataset-group`, `create-dataset-import-job`, `describe-dataset-import-job`, `list-dataset-import-jobs`, `delete-dataset-import-job` |
| Predictors | [`predictors.md`](predictors.md) | `create-auto-predictor`, `create-predictor`, `describe-auto-predictor`, `describe-predictor`, `list-predictors`, `delete-predictor`, `get-accuracy-metrics` |
| Forecasts | [`forecasts.md`](forecasts.md) | `create-forecast`, `describe-forecast`, `list-forecasts`, `delete-forecast`, `create-forecast-export-job`, `describe-forecast-export-job`, `list-forecast-export-jobs`, `delete-forecast-export-job` |
| Explainability | [`explainability.md`](explainability.md) | `create-explainability`, `describe-explainability`, `list-explainabilities`, `delete-explainability`, `create-explainability-export`, `describe-explainability-export`, `list-explainability-exports`, `delete-explainability-export` |
| Monitors | [`monitors.md`](monitors.md) | `create-monitor`, `describe-monitor`, `list-monitors`, `list-monitor-evaluations`, `delete-monitor` |
| What-If | [`what-if.md`](what-if.md) | `create-what-if-analysis`, `describe-what-if-analysis`, `list-what-if-analyses`, `delete-what-if-analysis`, `create-what-if-forecast`, `describe-what-if-forecast`, `list-what-if-forecasts`, `delete-what-if-forecast`, `create-what-if-forecast-export`, `describe-what-if-forecast-export`, `list-what-if-forecast-exports`, `delete-what-if-forecast-export` |
| Backtest Exports | [`backtest-exports.md`](backtest-exports.md) | `create-predictor-backtest-export-job`, `describe-predictor-backtest-export-job`, `list-predictor-backtest-export-jobs`, `delete-predictor-backtest-export-job` |
| Operations | [`operations.md`](operations.md) | `stop-resource`, `resume-resource`, `delete-resource-tree` |
| Queries | [`queries.md`](queries.md) | `query-forecast`, `query-what-if-forecast` (via `aws forecastquery`) |
| Tags | [`tags.md`](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
