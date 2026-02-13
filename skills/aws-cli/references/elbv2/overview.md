
# AWS CLI v2 — ELBv2 (Elastic Load Balancing v2)

## Overview

Complete reference for all `aws elbv2` subcommands in AWS CLI v2. Covers Application Load Balancers (ALB), Network Load Balancers (NLB), Gateway Load Balancers (GWLB), target groups, listeners, listener rules, health checks, SSL certificates, and WAF integration.

## Quick Reference — Common Workflows

### Create ALB for ECS
```bash
aws elbv2 create-load-balancer --name my-alb --type application \
  --subnets subnet-aaa subnet-bbb --security-groups sg-xxx
```

### Create target group (IP type for awsvpc network mode)
```bash
aws elbv2 create-target-group --name my-tg --protocol HTTP --port 80 \
  --vpc-id vpc-xxx --target-type ip \
  --health-check-path /health --health-check-interval-seconds 30
```

### Create HTTPS listener with default action
```bash
aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:... \
  --protocol HTTPS --port 443 \
  --certificates CertificateArn=arn:aws:acm:... \
  --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:...
```

### Create path-based routing rule
```bash
aws elbv2 create-rule --listener-arn arn:aws:elasticloadbalancing:... \
  --conditions Field=path-pattern,Values='/api/*' \
  --actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:... \
  --priority 10
```

### Describe target health
```bash
aws elbv2 describe-target-health --target-group-arn arn:aws:elasticloadbalancing:...
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Load Balancers | create, delete, describe, modify, set-subnets, set-security-groups, set-ip-address-type | ALB/NLB/GWLB lifecycle |
| Target Groups | create, delete, describe, modify, register/deregister targets, describe-target-health | Target management |
| Listeners | create, delete, describe, modify | Listener configuration |
| Rules | create, delete, describe, modify, set-rule-priorities | Routing rules |
| Certificates | add, remove, describe listener certificates | SSL/TLS management |
| Attributes | describe/modify load-balancer-attributes, describe/modify target-group-attributes | Feature configuration |
| Tags | add-tags, remove-tags, describe-tags | Resource tagging |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Load Balancers | [`load-balancers.md`](load-balancers.md) | create-load-balancer, delete-load-balancer, describe-load-balancers, modify-load-balancer-attributes, describe-load-balancer-attributes, set-subnets, set-security-groups, set-ip-address-type, get-resource-policy, describe-capacity-reservation, modify-capacity-reservation, modify-ip-pools |
| Target Groups | [`target-groups.md`](target-groups.md) | create-target-group, delete-target-group, describe-target-groups, modify-target-group, modify-target-group-attributes, describe-target-group-attributes, register-targets, deregister-targets, describe-target-health |
| Listeners | [`listeners.md`](listeners.md) | create-listener, delete-listener, describe-listeners, modify-listener, describe-listener-attributes, modify-listener-attributes |
| Rules | [`rules.md`](rules.md) | create-rule, delete-rule, describe-rules, modify-rule, set-rule-priorities |
| Certificates | [`certificates.md`](certificates.md) | add-listener-certificates, remove-listener-certificates, describe-listener-certificates |
| SSL Policies | [`ssl-policies.md`](ssl-policies.md) | describe-ssl-policies |
| Trust Stores | [`trust-stores.md`](trust-stores.md) | create-trust-store, delete-trust-store, describe-trust-stores, modify-trust-store, get-trust-store-ca-certificates-bundle, describe-trust-store-associations, add-trust-store-revocations, remove-trust-store-revocations, describe-trust-store-revocations, get-trust-store-revocation-content, delete-shared-trust-store-association |
| Tags | [`tags.md`](tags.md) | add-tags, remove-tags, describe-tags |
| Account Limits | [`account-limits.md`](account-limits.md) | describe-account-limits |
| Wait Commands | [`wait-commands.md`](wait-commands.md) | wait load-balancer-available, wait load-balancer-exists, wait load-balancers-deleted, wait target-deregistered, wait target-in-service |
