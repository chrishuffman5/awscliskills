# Utilization

Service Quotas integrates with CloudWatch to provide usage metrics for many quotas. This page covers how to retrieve and monitor quota utilization.

## Checking Quota Usage

### Quotas with Usage Metrics

Some quotas include `UsageMetric` information that maps to CloudWatch metrics:

```bash
aws service-quotas get-service-quota \
  --service-code ec2 \
  --quota-code L-1216C47A \
  --query 'Quota.{Name:QuotaName,Value:Value,Usage:UsageMetric}'
```

### Usage Metric Structure

When a quota has usage tracking enabled, the `UsageMetric` field contains:

```json
{
    "UsageMetric": {
        "MetricNamespace": "AWS/Usage",
        "MetricName": "ResourceCount",
        "MetricDimensions": {
            "Class": "None",
            "Resource": "vCPU",
            "Service": "EC2",
            "Type": "Resource"
        },
        "MetricStatisticRecommendation": "Maximum"
    }
}
```

### Querying Usage via CloudWatch

Use the usage metric information to query CloudWatch directly:

```bash
aws cloudwatch get-metric-statistics \
  --namespace AWS/Usage \
  --metric-name ResourceCount \
  --dimensions Name=Class,Value=None Name=Resource,Value=vCPU Name=Service,Value=EC2 Name=Type,Value=Resource \
  --start-time 2024-01-01T00:00:00Z \
  --end-time 2024-01-02T00:00:00Z \
  --period 3600 \
  --statistics Maximum
```

### Listing Quotas with Usage Information

```bash
# List all quotas with their usage metric availability
aws service-quotas list-service-quotas --service-code ec2 \
  --query 'Quotas[?UsageMetric!=`null`].{Name:QuotaName,Code:QuotaCode,Value:Value,MetricName:UsageMetric.MetricName}'
```

## Setting Up CloudWatch Alarms for Quota Usage

Create a CloudWatch alarm to notify when approaching a quota limit:

```bash
# Step 1: Get the quota and its usage metric
aws service-quotas get-service-quota \
  --service-code ec2 \
  --quota-code L-1216C47A

# Step 2: Create alarm at 80% utilization
aws cloudwatch put-metric-alarm \
  --alarm-name ec2-vcpu-quota-alarm \
  --alarm-description "EC2 vCPU usage at 80% of quota" \
  --namespace AWS/Usage \
  --metric-name ResourceCount \
  --dimensions Name=Class,Value=None Name=Resource,Value=vCPU Name=Service,Value=EC2 Name=Type,Value=Resource \
  --statistic Maximum \
  --period 300 \
  --threshold 80 \
  --comparison-operator GreaterThanOrEqualToThreshold \
  --evaluation-periods 1 \
  --alarm-actions arn:aws:sns:us-east-1:123456789012:quota-alerts
```

## Quota Utilization Reports

### Comparing Usage Against Quotas

```bash
# Get applied quota value and check against CloudWatch usage
SERVICE="ec2"
QUOTA_CODE="L-1216C47A"

# Get quota value
aws service-quotas get-service-quota \
  --service-code $SERVICE \
  --quota-code $QUOTA_CODE \
  --query 'Quota.Value' --output text

# Get current usage from CloudWatch
aws cloudwatch get-metric-statistics \
  --namespace AWS/Usage \
  --metric-name ResourceCount \
  --dimensions Name=Service,Value=EC2 Name=Resource,Value=vCPU Name=Type,Value=Resource Name=Class,Value=None \
  --start-time $(date -u -d '1 hour ago' +%Y-%m-%dT%H:%M:%SZ) \
  --end-time $(date -u +%Y-%m-%dT%H:%M:%SZ) \
  --period 3600 \
  --statistics Maximum \
  --query 'Datapoints[0].Maximum' --output text
```
