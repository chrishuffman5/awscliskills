# AWS CLI v2 — ELB (Elastic Load Balancing Classic)

## Overview

Complete reference for all `aws elb` subcommands in AWS CLI v2. Covers Classic Load Balancer creation and management, listeners, health checks, stickiness policies, security groups, subnets, availability zones, and tags.

## Quick Reference — Common Workflows

### Create a Classic Load Balancer
```bash
aws elb create-load-balancer --load-balancer-name my-clb \
  --listeners "Protocol=HTTP,LoadBalancerPort=80,InstanceProtocol=HTTP,InstancePort=80" \
  --availability-zones us-east-1a us-east-1b
```

### Create a VPC-based Classic Load Balancer
```bash
aws elb create-load-balancer --load-balancer-name my-clb \
  --listeners "Protocol=HTTP,LoadBalancerPort=80,InstanceProtocol=HTTP,InstancePort=80" \
  --subnets subnet-0123456789abcdef0 subnet-abcdef0123456789a \
  --security-groups sg-0123456789abcdef0
```

### Configure a health check
```bash
aws elb configure-health-check --load-balancer-name my-clb \
  --health-check Target=HTTP:80/health,Interval=30,UnhealthyThreshold=2,HealthyThreshold=10,Timeout=5
```

### Register instances
```bash
aws elb register-instances-with-load-balancer --load-balancer-name my-clb \
  --instances i-0123456789abcdef0 i-abcdef0123456789a
```

### Check instance health
```bash
aws elb describe-instance-health --load-balancer-name my-clb
```

### Enable sticky sessions (LB-generated cookie)
```bash
aws elb create-lb-cookie-stickiness-policy --load-balancer-name my-clb \
  --policy-name my-sticky-policy --cookie-expiration-period 60
aws elb set-load-balancer-policies-of-listener --load-balancer-name my-clb \
  --load-balancer-port 80 --policy-names my-sticky-policy
```

### Add HTTPS listener with SSL certificate
```bash
aws elb create-load-balancer-listeners --load-balancer-name my-clb \
  --listeners "Protocol=HTTPS,LoadBalancerPort=443,InstanceProtocol=HTTP,InstancePort=80,SSLCertificateId=arn:aws:acm:us-east-1:123456789012:certificate/abc-123"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Load Balancers | [`load-balancers.md`](load-balancers.md) | create-load-balancer, delete-load-balancer, describe-load-balancers, describe-load-balancer-attributes, modify-load-balancer-attributes, describe-account-limits |
| Listeners | [`listeners.md`](listeners.md) | create-load-balancer-listeners, delete-load-balancer-listeners, set-load-balancer-listener-ssl-certificate |
| Instances | [`instances.md`](instances.md) | register-instances-with-load-balancer, deregister-instances-from-load-balancer, describe-instance-health, configure-health-check |
| Policies | [`policies.md`](policies.md) | create-load-balancer-policy, delete-load-balancer-policy, describe-load-balancer-policies, describe-load-balancer-policy-types, create-app-cookie-stickiness-policy, create-lb-cookie-stickiness-policy, set-load-balancer-policies-of-listener, set-load-balancer-policies-for-backend-server |
| Networking | [`networking.md`](networking.md) | apply-security-groups-to-load-balancer, attach-load-balancer-to-subnets, detach-load-balancer-from-subnets, enable-availability-zones-for-load-balancer, disable-availability-zones-for-load-balancer |
| Tags | [`tags.md`](tags.md) | add-tags, remove-tags, describe-tags |
| Wait | [`wait.md`](wait.md) | wait any-instance-in-service, wait instance-deregistered, wait instance-in-service |
