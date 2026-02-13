# AWS CLI v2 — Budgets

## Overview

Complete reference for all `aws budgets` subcommands in AWS CLI v2. Covers budget creation and management, budget actions (auto-remediation via IAM policies, SCPs, or SSM documents), notifications, subscribers, and budget performance history.

## Quick Reference — Common Workflows

### Create a monthly cost budget with notification
```bash
aws budgets create-budget \
  --account-id 111122223333 \
  --budget file://budget.json \
  --notifications-with-subscribers file://notifications.json
```

### Describe a budget
```bash
aws budgets describe-budget \
  --account-id 111122223333 \
  --budget-name "Monthly-Cost-Budget"
```

### Create a budget action (auto-apply IAM policy at threshold)
```bash
aws budgets create-budget-action \
  --account-id 111122223333 \
  --budget-name "Monthly-Cost-Budget" \
  --notification-type ACTUAL \
  --action-type APPLY_IAM_POLICY \
  --action-threshold ActionThresholdValue=100,ActionThresholdType=PERCENTAGE \
  --definition '{"IamActionDefinition":{"PolicyArn":"arn:aws:iam::111122223333:policy/DenyAll","Users":["dev-user"]}}' \
  --execution-role-arn arn:aws:iam::111122223333:role/BudgetActionRole \
  --approval-model MANUAL \
  --subscribers SubscriptionType=EMAIL,Address=admin@example.com
```

### Add a notification to an existing budget
```bash
aws budgets create-notification \
  --account-id 111122223333 \
  --budget-name "Monthly-Cost-Budget" \
  --notification NotificationType=ACTUAL,ComparisonOperator=GREATER_THAN,Threshold=80,ThresholdType=PERCENTAGE \
  --subscribers SubscriptionType=EMAIL,Address=team@example.com
```

### View budget performance history
```bash
aws budgets describe-budget-performance-history \
  --account-id 111122223333 \
  --budget-name "Monthly-Cost-Budget" \
  --time-period Start=2025-01-01,End=2025-06-01
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Budgets | [`budgets.md`](budgets.md) | create-budget, delete-budget, describe-budget, describe-budgets, update-budget, describe-budget-performance-history |
| Budget Actions | [`budget-actions.md`](budget-actions.md) | create-budget-action, delete-budget-action, describe-budget-action, update-budget-action, execute-budget-action, describe-budget-action-histories, describe-budget-actions-for-account, describe-budget-actions-for-budget |
| Notifications | [`notifications.md`](notifications.md) | create-notification, delete-notification, update-notification, describe-notifications-for-budget, describe-budget-notifications-for-account |
| Subscribers | [`subscribers.md`](subscribers.md) | create-subscriber, delete-subscriber, update-subscriber, describe-subscribers-for-notification |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
