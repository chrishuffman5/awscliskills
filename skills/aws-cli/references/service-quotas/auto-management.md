# Auto Management

Service Quotas can automatically apply quota increases when they are available. This page covers the auto-applied quota patterns and how to check them.

## Checking Auto-Adjustable Quotas

### Identifying Adjustable Quotas

Use `list-service-quotas` and filter for adjustable quotas:

```bash
aws service-quotas list-service-quotas --service-code ec2 \
  --query 'Quotas[?Adjustable==`true`].{Name:QuotaName,Code:QuotaCode,Value:Value,Unit:Unit}'
```

### Checking Applied vs Default Values

Compare the applied value against the AWS default to see which quotas have been increased:

```bash
# Get the applied (current) value
aws service-quotas get-service-quota \
  --service-code ec2 \
  --quota-code L-1216C47A \
  --query 'Quota.{Name:QuotaName,AppliedValue:Value}'

# Get the AWS default value
aws service-quotas get-aws-default-service-quota \
  --service-code ec2 \
  --quota-code L-1216C47A \
  --query 'Quota.{Name:QuotaName,DefaultValue:Value}'
```

### Quota Applied At Level

Some quotas are applied at account level while others can be applied at the resource level:

| Level | Description |
|-------|-------------|
| `ACCOUNT` | Quota applies to the entire account |
| `RESOURCE` | Quota applies to individual resources |
| `ALL` | Quota applies at all levels |

```bash
# List resource-level quotas
aws service-quotas list-service-quotas --service-code ec2 \
  --quota-applied-at-level RESOURCE \
  --query 'Quotas[].{Name:QuotaName,Code:QuotaCode,Value:Value}'
```

### Organization Template Auto-Application

When the quota template is associated with an organization, new accounts automatically receive quota increase requests:

```bash
# Check if template is associated
aws service-quotas get-association-for-service-quota-template

# List all template entries (auto-applied to new accounts)
aws service-quotas list-service-quota-increase-requests-in-template
```

## Quota Period

Some quotas have rate-based periods. Check the period to understand if a quota is rate-limited:

```bash
aws service-quotas get-service-quota \
  --service-code lambda \
  --quota-code L-B99A9384 \
  --query 'Quota.{Name:QuotaName,Value:Value,Period:Period}'
```

### Period Units
| Unit | Description |
|------|-------------|
| `MICROSECOND` | Per microsecond |
| `MILLISECOND` | Per millisecond |
| `SECOND` | Per second |
| `MINUTE` | Per minute |
| `HOUR` | Per hour |
| `DAY` | Per day |
| `WEEK` | Per week |
