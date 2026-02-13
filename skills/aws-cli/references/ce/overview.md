# AWS CLI v2 — Cost Explorer

## Overview

Complete reference for all `aws ce` subcommands in AWS CLI v2. Covers cost and usage analysis, cost forecasting, anomaly detection, cost category management, reservation analysis, savings plans recommendations, rightsizing recommendations, commitment purchase analysis, and cost allocation tag management.

## Quick Reference — Common Workflows

### Get monthly cost by service
```bash
aws ce get-cost-and-usage \
  --time-period Start=2025-01-01,End=2025-02-01 \
  --granularity MONTHLY \
  --metrics "UnblendedCost" \
  --group-by Type=DIMENSION,Key=SERVICE
```

### Forecast upcoming costs
```bash
aws ce get-cost-forecast \
  --time-period Start=2025-02-01,End=2025-05-01 \
  --metric UNBLENDED_COST \
  --granularity MONTHLY
```

### Check for cost anomalies
```bash
aws ce get-anomalies \
  --date-interval StartDate=2025-01-01,EndDate=2025-01-31 \
  --total-impact NumericOperator=GREATER_THAN_OR_EQUAL,StartValue=100
```

### Create a cost anomaly monitor
```bash
aws ce create-anomaly-monitor \
  --anomaly-monitor MonitorName=ServiceMonitor,MonitorType=DIMENSIONAL,MonitorDimension=SERVICE
```

### Get rightsizing recommendations
```bash
aws ce get-rightsizing-recommendation \
  --service AmazonEC2 \
  --configuration RecommendationTarget=SAME_INSTANCE_FAMILY,BenefitsConsidered=true
```

### List cost allocation tags
```bash
aws ce list-cost-allocation-tags --status Active --type UserDefined
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Cost & Usage | [`cost-usage.md`](cost-usage.md) | get-cost-and-usage, get-cost-and-usage-with-resources, get-cost-and-usage-comparisons, get-cost-comparison-drivers, get-cost-forecast, get-usage-forecast, get-dimension-values, get-tags, get-approximate-usage-records |
| Cost Categories | [`cost-categories.md`](cost-categories.md) | create-cost-category-definition, delete-cost-category-definition, describe-cost-category-definition, update-cost-category-definition, get-cost-categories, list-cost-category-definitions, list-cost-category-resource-associations |
| Anomalies | [`anomalies.md`](anomalies.md) | create-anomaly-monitor, delete-anomaly-monitor, get-anomaly-monitors, update-anomaly-monitor, create-anomaly-subscription, delete-anomaly-subscription, get-anomaly-subscriptions, update-anomaly-subscription, get-anomalies, provide-anomaly-feedback |
| Reservations | [`reservations.md`](reservations.md) | get-reservation-coverage, get-reservation-purchase-recommendation, get-reservation-utilization |
| Savings Plans | [`savings-plans.md`](savings-plans.md) | get-savings-plans-coverage, get-savings-plans-purchase-recommendation, get-savings-plans-utilization, get-savings-plans-utilization-details, get-savings-plan-purchase-recommendation-details, list-savings-plans-purchase-recommendation-generation, start-savings-plans-purchase-recommendation-generation |
| Rightsizing | [`rightsizing.md`](rightsizing.md) | get-rightsizing-recommendation |
| Commitment Analysis | [`commitment-analysis.md`](commitment-analysis.md) | start-commitment-purchase-analysis, get-commitment-purchase-analysis, list-commitment-purchase-analyses |
| Cost Allocation Tags | [`cost-allocation-tags.md`](cost-allocation-tags.md) | list-cost-allocation-tags, update-cost-allocation-tags-status, list-cost-allocation-tag-backfill-history, start-cost-allocation-tag-backfill |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
