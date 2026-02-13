# AWS CLI v2 — Route 53 Application Recovery Controller

## Overview

Complete reference for `aws route53-recovery-cluster`, `aws route53-recovery-control-config`, and `aws route53-recovery-readiness` subcommands in AWS CLI v2. Route 53 Application Recovery Controller (ARC) provides readiness checks, routing controls, and failover capabilities to help you build applications with high availability. The three APIs cover: data plane operations for routing control state (recovery-cluster), control plane configuration for clusters/panels/rules (recovery-control-config), and readiness assessment for recovery preparedness (recovery-readiness).

## Quick Reference — Common Workflows

### Create a recovery cluster and control panel
```bash
aws route53-recovery-control-config create-cluster \
  --cluster-name my-cluster

aws route53-recovery-control-config wait cluster-created \
  --cluster-arn arn:aws:route53-recovery-control-config::123456789012:cluster/abc123

aws route53-recovery-control-config create-control-panel \
  --cluster-arn arn:aws:route53-recovery-control-config::123456789012:cluster/abc123 \
  --control-panel-name my-panel
```

### Create routing controls and set state
```bash
aws route53-recovery-control-config create-routing-control \
  --cluster-arn arn:aws:route53-recovery-control-config::123456789012:cluster/abc123 \
  --routing-control-name us-east-1-cell \
  --control-panel-arn arn:aws:route53-recovery-control-config::123456789012:controlpanel/def456

aws route53-recovery-cluster update-routing-control-state \
  --routing-control-arn arn:aws:route53-recovery-control-config::123456789012:routingcontrol/ghi789 \
  --routing-control-state On \
  --region us-west-2
```

### Check routing control state
```bash
aws route53-recovery-cluster get-routing-control-state \
  --routing-control-arn arn:aws:route53-recovery-control-config::123456789012:routingcontrol/ghi789 \
  --region us-west-2
```

### Create a safety rule (assertion)
```bash
aws route53-recovery-control-config create-safety-rule \
  --assertion-rule '{
    "ControlPanelArn": "arn:aws:route53-recovery-control-config::123456789012:controlpanel/def456",
    "AssertedControls": ["arn:aws:...routingcontrol/rc1", "arn:aws:...routingcontrol/rc2"],
    "Name": "AtLeastOneOn",
    "RuleConfig": {"Type": "ATLEAST", "Threshold": 1, "Inverted": false},
    "WaitPeriodMs": 5000
  }'
```

### Set up readiness checks
```bash
aws route53-recovery-readiness create-recovery-group \
  --recovery-group-name my-recovery-group

aws route53-recovery-readiness create-cell --cell-name us-east-1-cell
aws route53-recovery-readiness create-cell --cell-name us-west-2-cell

aws route53-recovery-readiness create-resource-set \
  --resource-set-name my-nlb-set \
  --resource-set-type AWS::ElasticLoadBalancingV2::LoadBalancer \
  --resources '[{"ResourceArn":"arn:aws:elasticloadbalancing:us-east-1:123456789012:loadbalancer/net/my-nlb/abc123","ReadinessScopes":["arn:aws:route53-recovery-readiness::123456789012:cell/us-east-1-cell"]}]'

aws route53-recovery-readiness create-readiness-check \
  --readiness-check-name my-nlb-check \
  --resource-set-name my-nlb-set
```

### Get readiness status
```bash
aws route53-recovery-readiness get-readiness-check-status \
  --readiness-check-name my-nlb-check

aws route53-recovery-readiness get-recovery-group-readiness-summary \
  --recovery-group-name my-recovery-group
```

### Failover with safety rule override (break glass)
```bash
aws route53-recovery-cluster update-routing-control-states \
  --update-routing-control-state-entries \
    RoutingControlArn=arn:aws:...routingcontrol/rc1,RoutingControlState=Off \
    RoutingControlArn=arn:aws:...routingcontrol/rc2,RoutingControlState=On \
  --safety-rules-to-override arn:aws:...safetyrule/sr1 \
  --region us-west-2
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Routing Controls | [`routing-controls.md`](routing-controls.md) | get-routing-control-state, list-routing-controls, update-routing-control-state, update-routing-control-states, create-routing-control, delete-routing-control, describe-routing-control, update-routing-control, list-routing-controls (config), list-associated-route53-health-checks |
| Clusters | [`clusters.md`](clusters.md) | create-cluster, delete-cluster, describe-cluster, list-clusters, update-cluster |
| Control Panels | [`control-panels.md`](control-panels.md) | create-control-panel, delete-control-panel, describe-control-panel, update-control-panel, list-control-panels |
| Safety Rules | [`safety-rules.md`](safety-rules.md) | create-safety-rule, delete-safety-rule, describe-safety-rule, update-safety-rule, list-safety-rules |
| Readiness Checks | [`readiness-checks.md`](readiness-checks.md) | create-readiness-check, get-readiness-check, update-readiness-check, delete-readiness-check, list-readiness-checks, get-readiness-check-status, get-readiness-check-resource-status |
| Recovery Groups | [`recovery-groups.md`](recovery-groups.md) | create-recovery-group, get-recovery-group, update-recovery-group, delete-recovery-group, list-recovery-groups, get-recovery-group-readiness-summary, get-architecture-recommendations |
| Cells | [`cells.md`](cells.md) | create-cell, get-cell, update-cell, delete-cell, list-cells, get-cell-readiness-summary |
| Resource Sets | [`resource-sets.md`](resource-sets.md) | create-resource-set, get-resource-set, update-resource-set, delete-resource-set, list-resource-sets, list-rules |
| Cross-Account & Tags | [`cross-account-tags.md`](cross-account-tags.md) | create-cross-account-authorization, delete-cross-account-authorization, list-cross-account-authorizations, tag-resource, untag-resource, list-tags-for-resource, list-tags-for-resources, get-resource-policy |
| Wait | [`wait.md`](wait.md) | wait cluster-created, wait cluster-deleted, wait control-panel-created, wait control-panel-deleted, wait routing-control-created, wait routing-control-deleted |
