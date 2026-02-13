# AWS CLI v2 — EKS (Elastic Kubernetes Service)

## Overview

Complete reference for all `aws eks` subcommands in AWS CLI v2. Covers EKS cluster management, managed node groups, Fargate profiles, add-ons, access management, identity provider configs, Pod Identity associations, encryption and insights, capabilities, EKS Anywhere subscriptions, updates, tags, and wait commands.

## Quick Reference — Common Workflows

### Create an EKS cluster
```bash
aws eks create-cluster --name my-cluster \
  --role-arn arn:aws:iam::123456789012:role/EKSClusterRole \
  --resources-vpc-config subnetIds=subnet-abc123,subnet-def456,securityGroupIds=sg-12345 \
  --kubernetes-version 1.29
aws eks wait cluster-active --name my-cluster
```

### Create a managed node group
```bash
aws eks create-nodegroup --cluster-name my-cluster \
  --nodegroup-name my-nodes --node-role arn:aws:iam::123456789012:role/EKSNodeRole \
  --subnets subnet-abc123 subnet-def456 \
  --instance-types t3.medium --scaling-config minSize=2,maxSize=5,desiredSize=3
aws eks wait nodegroup-active --cluster-name my-cluster --nodegroup-name my-nodes
```

### Create a Fargate profile
```bash
aws eks create-fargate-profile --cluster-name my-cluster \
  --fargate-profile-name my-fargate --pod-execution-role-arn arn:aws:iam::123456789012:role/EKSFargatePodRole \
  --subnets subnet-abc123 \
  --selectors namespace=my-namespace
aws eks wait fargate-profile-active --cluster-name my-cluster \
  --fargate-profile-name my-fargate
```

### Install an add-on
```bash
aws eks create-addon --cluster-name my-cluster \
  --addon-name vpc-cni --addon-version v1.16.0-eksbuild.1 \
  --service-account-role-arn arn:aws:iam::123456789012:role/VPCCNIRole
aws eks wait addon-active --cluster-name my-cluster --addon-name vpc-cni
```

### Update kubeconfig
```bash
aws eks update-kubeconfig --name my-cluster --region us-east-1
```

### Grant cluster access
```bash
aws eks create-access-entry --cluster-name my-cluster \
  --principal-arn arn:aws:iam::123456789012:role/DevRole
aws eks associate-access-policy --cluster-name my-cluster \
  --principal-arn arn:aws:iam::123456789012:role/DevRole \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSClusterAdminPolicy \
  --access-scope type=cluster
```

### Create Pod Identity association
```bash
aws eks create-pod-identity-association --cluster-name my-cluster \
  --namespace my-namespace --service-account my-sa \
  --role-arn arn:aws:iam::123456789012:role/PodRole
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-cluster, delete-cluster, describe-cluster, describe-cluster-versions, list-clusters, update-cluster-config, update-cluster-version, register-cluster, deregister-cluster, update-kubeconfig, get-token |
| Node Groups | [`nodegroups.md`](nodegroups.md) | create-nodegroup, delete-nodegroup, describe-nodegroup, list-nodegroups, update-nodegroup-config, update-nodegroup-version |
| Fargate Profiles | [`fargate-profiles.md`](fargate-profiles.md) | create-fargate-profile, delete-fargate-profile, describe-fargate-profile, list-fargate-profiles |
| Add-ons | [`addons.md`](addons.md) | create-addon, delete-addon, describe-addon, describe-addon-versions, describe-addon-configuration, list-addons, update-addon |
| Access Management | [`access-management.md`](access-management.md) | create-access-entry, delete-access-entry, describe-access-entry, list-access-entries, update-access-entry, associate-access-policy, disassociate-access-policy, list-associated-access-policies, list-access-policies |
| Identity Providers | [`identity-providers.md`](identity-providers.md) | associate-identity-provider-config, disassociate-identity-provider-config, describe-identity-provider-config, list-identity-provider-configs |
| Pod Identity | [`pod-identity.md`](pod-identity.md) | create-pod-identity-association, delete-pod-identity-association, describe-pod-identity-association, list-pod-identity-associations, update-pod-identity-association |
| Encryption & Insights | [`encryption-insights.md`](encryption-insights.md) | associate-encryption-config, describe-insight, list-insights |
| Capabilities | [`capabilities.md`](capabilities.md) | create-capability, delete-capability, describe-capability, list-capabilities, update-capability |
| EKS Anywhere | [`eks-anywhere.md`](eks-anywhere.md) | create-eks-anywhere-subscription, delete-eks-anywhere-subscription, describe-eks-anywhere-subscription, list-eks-anywhere-subscriptions, update-eks-anywhere-subscription |
| Updates & Tags | [`updates-tags.md`](updates-tags.md) | describe-update, list-updates, tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait cluster-active, wait cluster-deleted, wait nodegroup-active, wait nodegroup-deleted, wait addon-active, wait addon-deleted, wait fargate-profile-active, wait fargate-profile-deleted |
