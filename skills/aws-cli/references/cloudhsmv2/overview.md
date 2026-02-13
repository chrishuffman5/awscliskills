# AWS CLI v2 — CloudHSM (AWS CloudHSM v2)

## Overview

Complete reference for all `aws cloudhsmv2` subcommands in AWS CLI v2. Covers CloudHSM cluster lifecycle management, HSM instance provisioning and deletion, backup management (create, copy, restore, delete), cluster initialization, resource policy management, and tagging.

## Quick Reference — Common Workflows

### Create a CloudHSM cluster
```bash
aws cloudhsmv2 create-cluster \
  --hsm-type hsm1.medium \
  --subnet-ids subnet-0123456789abcdef0 subnet-0123456789abcdef1 \
  --tag-list Key=Environment,Value=production
```

### Add an HSM to a cluster
```bash
aws cloudhsmv2 create-hsm \
  --cluster-id cluster-abcdefg1234 \
  --availability-zone us-east-1a
```

### Initialize a cluster (after signing the CSR)
```bash
aws cloudhsmv2 initialize-cluster \
  --cluster-id cluster-abcdefg1234 \
  --signed-cert fileb://signed-cert.pem \
  --trust-anchor fileb://trust-anchor.pem
```

### Describe clusters with filters
```bash
aws cloudhsmv2 describe-clusters \
  --filters clusterIds=cluster-abcdefg1234

aws cloudhsmv2 describe-clusters \
  --filters states=ACTIVE
```

### Copy a backup to another region
```bash
aws cloudhsmv2 copy-backup-to-region \
  --destination-region us-west-2 \
  --backup-id backup-abcdefg1234
```

### Restore a cluster from backup
```bash
aws cloudhsmv2 create-cluster \
  --hsm-type hsm1.medium \
  --source-backup-id backup-abcdefg1234 \
  --subnet-ids subnet-0123456789abcdef0
```

### Delete an HSM and cluster
```bash
aws cloudhsmv2 delete-hsm \
  --cluster-id cluster-abcdefg1234 \
  --hsm-id hsm-abcdefg1234

aws cloudhsmv2 delete-cluster \
  --cluster-id cluster-abcdefg1234
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-cluster, delete-cluster, describe-clusters, modify-cluster, initialize-cluster |
| HSMs | [`hsms.md`](hsms.md) | create-hsm, delete-hsm |
| Backups | [`backups.md`](backups.md) | describe-backups, delete-backup, copy-backup-to-region, restore-backup, modify-backup-attributes |
| Policies & Tags | [`policies-tags.md`](policies-tags.md) | get-resource-policy, put-resource-policy, delete-resource-policy, tag-resource, untag-resource, list-tags |
