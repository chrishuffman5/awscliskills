# AWS CLI v2 — Network Firewall (AWS Network Firewall)

## Overview

Complete reference for all `aws network-firewall` subcommands in AWS CLI v2. Covers firewall creation and management, firewall policy configuration, stateful and stateless rule groups, TLS inspection, subnet and availability zone associations, VPC endpoint associations, transit gateway attachments, forward proxy, logging and analysis, resource policies, and tagging.

## Quick Reference — Common Workflows

### Create a firewall policy with stateless default actions
```bash
aws network-firewall create-firewall-policy \
  --firewall-policy-name my-policy \
  --firewall-policy '{"StatelessDefaultActions":["aws:forward_to_sfe"],"StatelessFragmentDefaultActions":["aws:forward_to_sfe"]}'
```

### Create a stateful rule group (Suricata format)
```bash
aws network-firewall create-rule-group \
  --rule-group-name my-stateful-rules \
  --type STATEFUL \
  --capacity 100 \
  --rules 'pass tls any any -> any any (tls.sni; content:"example.com"; sid:1; rev:1;)'
```

### Create a firewall
```bash
aws network-firewall create-firewall \
  --firewall-name my-firewall \
  --firewall-policy-arn arn:aws:network-firewall:us-east-1:123456789012:firewall-policy/my-policy \
  --vpc-id vpc-0123456789abcdef0 \
  --subnet-mappings SubnetId=subnet-0123456789abcdef0 SubnetId=subnet-0123456789abcdef1
```

### Update firewall policy with rule group references
```bash
aws network-firewall update-firewall-policy \
  --firewall-policy-arn arn:aws:network-firewall:us-east-1:123456789012:firewall-policy/my-policy \
  --update-token "$TOKEN" \
  --firewall-policy '{"StatelessDefaultActions":["aws:forward_to_sfe"],"StatelessFragmentDefaultActions":["aws:forward_to_sfe"],"StatefulRuleGroupReferences":[{"ResourceArn":"arn:aws:network-firewall:us-east-1:123456789012:stateful-rulegroup/my-stateful-rules"}]}'
```

### Configure logging
```bash
aws network-firewall update-logging-configuration \
  --firewall-arn arn:aws:network-firewall:us-east-1:123456789012:firewall/my-firewall \
  --logging-configuration '{"LogDestinationConfigs":[{"LogType":"ALERT","LogDestinationType":"CloudWatchLogs","LogDestination":{"logGroup":"alert-log-group"}},{"LogType":"FLOW","LogDestinationType":"S3","LogDestination":{"bucketName":"my-flow-logs","prefix":"network-firewall"}}]}'
```

### Associate additional subnets
```bash
aws network-firewall associate-subnets \
  --firewall-arn arn:aws:network-firewall:us-east-1:123456789012:firewall/my-firewall \
  --subnet-mappings SubnetId=subnet-0123456789abcdef2 \
  --update-token "$TOKEN"
```

### Describe a firewall
```bash
aws network-firewall describe-firewall \
  --firewall-name my-firewall
```

### Delete a firewall
```bash
aws network-firewall delete-firewall \
  --firewall-name my-firewall
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Firewalls | [`firewalls.md`](firewalls.md) | create-firewall, delete-firewall, describe-firewall, describe-firewall-metadata, list-firewalls, update-firewall-description, update-firewall-delete-protection, update-firewall-policy-change-protection, update-firewall-encryption-configuration, update-firewall-analysis-settings, update-availability-zone-change-protection, associate-firewall-policy |
| Firewall Policies | [`firewall-policies.md`](firewall-policies.md) | create-firewall-policy, delete-firewall-policy, describe-firewall-policy, list-firewall-policies, update-firewall-policy |
| Rule Groups | [`rule-groups.md`](rule-groups.md) | create-rule-group, delete-rule-group, describe-rule-group, describe-rule-group-metadata, list-rule-groups, update-rule-group |
| TLS Inspection | [`tls-inspection.md`](tls-inspection.md) | create-tls-inspection-configuration, delete-tls-inspection-configuration, describe-tls-inspection-configuration, list-tls-inspection-configurations, update-tls-inspection-configuration |
| Subnets & Zones | [`subnets-zones.md`](subnets-zones.md) | associate-subnets, disassociate-subnets, associate-availability-zones, disassociate-availability-zones, update-subnet-change-protection |
| VPC Endpoints | [`vpc-endpoints.md`](vpc-endpoints.md) | create-vpc-endpoint-association, delete-vpc-endpoint-association, describe-vpc-endpoint-association, list-vpc-endpoint-associations |
| Transit Gateway | [`transit-gateway.md`](transit-gateway.md) | accept-network-firewall-transit-gateway-attachment, delete-network-firewall-transit-gateway-attachment, reject-network-firewall-transit-gateway-attachment |
| Proxy | [`proxy.md`](proxy.md) | create-proxy, delete-proxy, describe-proxy, list-proxies, update-proxy, create-proxy-configuration, delete-proxy-configuration, describe-proxy-configuration, list-proxy-configurations, update-proxy-configuration |
| Logging & Analysis | [`logging-analysis.md`](logging-analysis.md) | describe-logging-configuration, update-logging-configuration, start-analysis-report, list-analysis-reports, get-analysis-report-results, describe-flow-operation, list-flow-operations, list-flow-operation-results, start-flow-capture, start-flow-flush |
| Resource Policies & Tags | [`resource-policies-tags.md`](resource-policies-tags.md) | describe-resource-policy, put-resource-policy, delete-resource-policy, tag-resource, untag-resource, list-tags-for-resource |
