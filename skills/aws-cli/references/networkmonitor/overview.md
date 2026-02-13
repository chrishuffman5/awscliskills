# AWS CLI v2 — CloudWatch Network Monitor

## Overview

Complete reference for all `aws networkmonitor` subcommands in AWS CLI v2. Amazon CloudWatch Network Monitor is an active network monitoring service that identifies network issues within the AWS network or your own company network, where hybrid connectivity allows for cross-network monitoring. It uses probes to test network connectivity from your VPC subnets to destinations, monitoring via TCP or ICMP protocols and reporting metrics to CloudWatch.

## Quick Reference — Common Workflows

### Create a monitor with a TCP probe
```bash
aws networkmonitor create-monitor \
  --monitor-name my-network-monitor \
  --aggregation-period 60 \
  --probes sourceArn=arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0123456789abcdef0,destination=10.0.0.100,destinationPort=443,protocol=TCP,packetSize=56
```

### Create a monitor with an ICMP probe
```bash
aws networkmonitor create-monitor \
  --monitor-name my-icmp-monitor \
  --aggregation-period 30 \
  --probes sourceArn=arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0123456789abcdef0,destination=10.0.0.100,protocol=ICMP,packetSize=56
```

### Add a probe to an existing monitor
```bash
aws networkmonitor create-probe \
  --monitor-name my-network-monitor \
  --probe sourceArn=arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0abcdef1234567890,destination=10.0.1.100,destinationPort=80,protocol=TCP,packetSize=56
```

### Get monitor details with probes
```bash
aws networkmonitor get-monitor --monitor-name my-network-monitor
```

### List all monitors
```bash
aws networkmonitor list-monitors \
  --query 'monitors[*].[monitorName,state,aggregationPeriod]' \
  --output table
```

### Update probe configuration
```bash
aws networkmonitor update-probe \
  --monitor-name my-network-monitor \
  --probe-id probe-0123456789abcdef0 \
  --destination 10.0.0.200 \
  --packet-size 100
```

### Delete a probe and monitor
```bash
aws networkmonitor delete-probe \
  --monitor-name my-network-monitor \
  --probe-id probe-0123456789abcdef0

aws networkmonitor delete-monitor \
  --monitor-name my-network-monitor
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Monitors | [`monitors.md`](monitors.md) | create-monitor, get-monitor, update-monitor, delete-monitor, list-monitors |
| Probes | [`probes.md`](probes.md) | create-probe, get-probe, update-probe, delete-probe |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
