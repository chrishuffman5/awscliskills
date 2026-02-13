# Forecast Quick Reference

## All Commands (`aws forecast`)

| Command | Description |
|---------|-------------|
| `create-auto-predictor` | Creates an AutoPredictor with automatic model selection |
| `create-dataset` | Creates a dataset for time-series data |
| `create-dataset-group` | Creates a dataset group linking datasets |
| `create-dataset-import-job` | Imports data from S3 into a dataset |
| `create-explainability` | Creates an Explainability resource for a predictor/forecast |
| `create-explainability-export` | Exports Explainability data to S3 |
| `create-forecast` | Generates a forecast from a predictor |
| `create-forecast-export-job` | Exports a forecast to S3 |
| `create-monitor` | Creates a predictor performance monitor |
| `create-predictor` | Creates a predictor (legacy, use create-auto-predictor) |
| `create-predictor-backtest-export-job` | Exports predictor backtest results to S3 |
| `create-what-if-analysis` | Creates a what-if scenario analysis |
| `create-what-if-forecast` | Creates a what-if forecast with transformations |
| `create-what-if-forecast-export` | Exports what-if forecast to S3 |
| `delete-dataset` | Deletes a dataset |
| `delete-dataset-group` | Deletes a dataset group |
| `delete-dataset-import-job` | Deletes a dataset import job |
| `delete-explainability` | Deletes an Explainability resource |
| `delete-explainability-export` | Deletes an Explainability export |
| `delete-forecast` | Deletes a forecast |
| `delete-forecast-export-job` | Deletes a forecast export job |
| `delete-monitor` | Deletes a predictor monitor |
| `delete-predictor` | Deletes a predictor |
| `delete-predictor-backtest-export-job` | Deletes a backtest export job |
| `delete-resource-tree` | Deletes a resource and all child resources |
| `delete-what-if-analysis` | Deletes a what-if analysis |
| `delete-what-if-forecast` | Deletes a what-if forecast |
| `delete-what-if-forecast-export` | Deletes a what-if forecast export |
| `describe-auto-predictor` | Gets properties of an AutoPredictor |
| `describe-dataset` | Gets properties of a dataset |
| `describe-dataset-group` | Gets properties of a dataset group |
| `describe-dataset-import-job` | Gets properties of a dataset import job |
| `describe-explainability` | Gets properties of an Explainability resource |
| `describe-explainability-export` | Gets properties of an Explainability export |
| `describe-forecast` | Gets properties of a forecast |
| `describe-forecast-export-job` | Gets properties of a forecast export job |
| `describe-monitor` | Gets properties of a predictor monitor |
| `describe-predictor` | Gets properties of a predictor |
| `describe-predictor-backtest-export-job` | Gets properties of a backtest export job |
| `describe-what-if-analysis` | Gets properties of a what-if analysis |
| `describe-what-if-forecast` | Gets properties of a what-if forecast |
| `describe-what-if-forecast-export` | Gets properties of a what-if forecast export |
| `get-accuracy-metrics` | Gets predictor accuracy metrics (WAPE, RMSE, MASE, MAPE) |
| `list-dataset-groups` | Lists dataset groups |
| `list-dataset-import-jobs` | Lists dataset import jobs |
| `list-datasets` | Lists datasets |
| `list-explainabilities` | Lists Explainability resources |
| `list-explainability-exports` | Lists Explainability exports |
| `list-forecast-export-jobs` | Lists forecast export jobs |
| `list-forecasts` | Lists forecasts |
| `list-monitor-evaluations` | Lists monitor evaluation results |
| `list-monitors` | Lists predictor monitors |
| `list-predictor-backtest-export-jobs` | Lists backtest export jobs |
| `list-predictors` | Lists predictors |
| `list-tags-for-resource` | Lists tags for a resource |
| `list-what-if-analyses` | Lists what-if analyses |
| `list-what-if-forecast-exports` | Lists what-if forecast exports |
| `list-what-if-forecasts` | Lists what-if forecasts |
| `resume-resource` | Resumes a stopped resource |
| `stop-resource` | Stops an in-progress resource creation |
| `tag-resource` | Adds tags to a resource |
| `untag-resource` | Removes tags from a resource |
| `update-dataset-group` | Updates datasets in a dataset group |

## Forecast Query Commands (`aws forecastquery`)

| Command | Description |
|---------|-------------|
| `query-forecast` | Queries a forecast for specific items and time range |
| `query-what-if-forecast` | Queries a what-if forecast for specific items and time range |

## Domains

| Domain | Description |
|--------|-------------|
| `RETAIL` | Retail demand forecasting |
| `CUSTOM` | Custom domain (any time-series) |
| `INVENTORY_PLANNING` | Inventory planning |
| `EC2_CAPACITY` | EC2 capacity planning |
| `WORK_FORCE` | Workforce planning |
| `WEB_TRAFFIC` | Web traffic forecasting |
| `METRICS` | General metrics forecasting |

## Dataset Types

| Type | Description |
|------|-------------|
| `TARGET_TIME_SERIES` | Primary time-series data (required) |
| `RELATED_TIME_SERIES` | Related time-series features |
| `ITEM_METADATA` | Static item attributes |

## Data Frequencies

Format: integer + unit. Examples: `1D`, `1H`, `15min`, `1W`, `1M`, `1Y`

| Unit | Description |
|------|-------------|
| `Y` | Yearly |
| `M` | Monthly |
| `W` | Weekly |
| `D` | Daily |
| `H` | Hourly |
| `30min` | Every 30 minutes |
| `15min` | Every 15 minutes |
| `10min` | Every 10 minutes |
| `5min` | Every 5 minutes |
| `1min` | Every minute |

## Optimization Metrics

| Metric | Description |
|--------|-------------|
| `WAPE` | Weighted Absolute Percentage Error |
| `RMSE` | Root Mean Squared Error |
| `AverageWeightedQuantileLoss` | Average weighted quantile loss |
| `MASE` | Mean Absolute Scaled Error |
| `MAPE` | Mean Absolute Percentage Error |

## Global Options

All `aws forecast` and `aws forecastquery` commands support these options:

| Option | Description |
|--------|-------------|
| `--region` | AWS region |
| `--profile` | Named profile |
| `--output` | Output format: `json`, `text`, `table`, `yaml` |
| `--query` | JMESPath query |
| `--no-cli-pager` | Disable pager |
| `--cli-input-json` | Read input from JSON |
| `--generate-cli-skeleton` | Generate input skeleton |
