# AWS CLI v2 — Auto Scaling

## Overview

Complete reference for all `aws autoscaling` subcommands in AWS CLI v2. Covers Auto Scaling groups, launch configurations, scaling policies (target tracking, step, simple), lifecycle hooks, scheduled actions, instance refresh, warm pools, load balancer integration, notifications, metrics collection, and tag management.

## Quick Reference — Common Workflows

### Create an Auto Scaling group
```bash
aws autoscaling create-auto-scaling-group --auto-scaling-group-name my-asg \
  --launch-template LaunchTemplateId=lt-0123456789abcdef0,Version='$Latest' \
  --min-size 1 --max-size 4 --desired-capacity 2 \
  --vpc-zone-identifier "subnet-abc123,subnet-def456" \
  --tags Key=Environment,Value=prod,PropagateAtLaunch=true
```

### Update desired capacity
```bash
aws autoscaling set-desired-capacity --auto-scaling-group-name my-asg \
  --desired-capacity 3
```

### Create a target tracking scaling policy
```bash
aws autoscaling put-scaling-policy --auto-scaling-group-name my-asg \
  --policy-name cpu-target-70 --policy-type TargetTrackingScaling \
  --target-tracking-configuration file://target-tracking.json
```

### Create a scheduled action
```bash
aws autoscaling put-scheduled-update-group-action \
  --auto-scaling-group-name my-asg \
  --scheduled-action-name scale-up-morning \
  --recurrence "0 8 * * MON-FRI" \
  --min-size 4 --max-size 10 --desired-capacity 6
```

### Start an instance refresh (rolling update)
```bash
aws autoscaling start-instance-refresh --auto-scaling-group-name my-asg \
  --preferences MinHealthyPercentage=90,InstanceWarmup=300
```

### Create a lifecycle hook
```bash
aws autoscaling put-lifecycle-hook --auto-scaling-group-name my-asg \
  --lifecycle-hook-name launch-hook \
  --lifecycle-transition autoscaling:EC2_INSTANCE_LAUNCHING \
  --heartbeat-timeout 300 --default-result CONTINUE
```

### Create a warm pool
```bash
aws autoscaling put-warm-pool --auto-scaling-group-name my-asg \
  --pool-state Stopped --min-size 2
```

### Attach/detach instances
```bash
aws autoscaling attach-instances --auto-scaling-group-name my-asg \
  --instance-ids i-0123456789abcdef0
aws autoscaling detach-instances --auto-scaling-group-name my-asg \
  --instance-ids i-0123456789abcdef0 --should-decrement-desired-capacity
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Groups | [`groups.md`](groups.md) | create-auto-scaling-group, update-auto-scaling-group, delete-auto-scaling-group, describe-auto-scaling-groups, set-desired-capacity, attach-instances, detach-instances, enter-standby, exit-standby, set-instance-protection, terminate-instance-in-auto-scaling-group, set-instance-health, describe-auto-scaling-instances, describe-scaling-activities, describe-adjustment-types |
| Launch Configurations | [`launch-configurations.md`](launch-configurations.md) | create-launch-configuration, delete-launch-configuration, describe-launch-configurations |
| Scaling Policies | [`scaling-policies.md`](scaling-policies.md) | put-scaling-policy, delete-policy, describe-policies, execute-policy, describe-scaling-process-types, suspend-processes, resume-processes |
| Lifecycle Hooks | [`lifecycle-hooks.md`](lifecycle-hooks.md) | put-lifecycle-hook, delete-lifecycle-hook, describe-lifecycle-hooks, describe-lifecycle-hook-types, complete-lifecycle-action, record-lifecycle-action-heartbeat |
| Scheduled Actions | [`scheduled-actions.md`](scheduled-actions.md) | put-scheduled-update-group-action, delete-scheduled-action, describe-scheduled-actions, batch-put-scheduled-update-group-action, batch-delete-scheduled-action |
| Instance Refresh | [`instance-refresh.md`](instance-refresh.md) | start-instance-refresh, cancel-instance-refresh, describe-instance-refreshes, rollback-instance-refresh |
| Warm Pool | [`warm-pool.md`](warm-pool.md) | put-warm-pool, delete-warm-pool, describe-warm-pool |
| Load Balancers | [`load-balancers.md`](load-balancers.md) | attach-load-balancers, detach-load-balancers, describe-load-balancers, attach-load-balancer-target-groups, detach-load-balancer-target-groups, describe-load-balancer-target-groups, attach-traffic-sources, detach-traffic-sources, describe-traffic-sources |
| Notifications & Metrics | [`notifications-metrics.md`](notifications-metrics.md) | put-notification-configuration, delete-notification-configuration, describe-notification-configurations, enable-metrics-collection, disable-metrics-collection, describe-metric-collection-types, describe-account-limits |
| Tags | [`tags.md`](tags.md) | create-or-update-tags, delete-tags, describe-tags |
