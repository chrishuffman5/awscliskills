# AWS CLI v2 — RAM (Resource Access Manager)

## Overview

Complete reference for all `aws ram` subcommands in AWS CLI v2. AWS Resource Access Manager (RAM) lets you share your resources with any AWS account or through AWS Organizations. RAM supports sharing of VPC subnets, Transit Gateways, Route 53 Resolver rules, License Manager configurations, and many other resource types across accounts and organizational units.

## Quick Reference — Common Workflows

### Create a resource share
```bash
aws ram create-resource-share --name my-share \
  --resource-arns arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0123456789abcdef0 \
  --principals 987654321098
```

### Accept a resource share invitation
```bash
aws ram accept-resource-share-invitation \
  --resource-share-invitation-arn arn:aws:ram:us-east-1:123456789012:resource-share-invitation/1234abcd-12ab-34cd-56ef-1234567890ab
```

### List resource shares
```bash
aws ram get-resource-shares --resource-owner SELF
aws ram get-resource-shares --resource-owner OTHER-ACCOUNTS
```

### Enable sharing with AWS Organizations
```bash
aws ram enable-sharing-with-aws-organization
```

### Add resources and principals to a share
```bash
aws ram associate-resource-share \
  --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/1234abcd-12ab-34cd-56ef-1234567890ab \
  --resource-arns arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0abcdef1234567890 \
  --principals 111222333444
```

### Create a custom permission
```bash
aws ram create-permission --name my-subnet-permission \
  --resource-type ec2:Subnet \
  --policy-template '{"Effect":"Allow","Action":["ec2:RunInstances","ec2:CreateNetworkInterface"]}'
```

### List shared resources
```bash
aws ram list-resources --resource-owner SELF
aws ram list-resources --resource-owner OTHER-ACCOUNTS
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Resource Shares | [`resource-shares.md`](resource-shares.md) | create-resource-share, update-resource-share, delete-resource-share, get-resource-shares, associate-resource-share, disassociate-resource-share, get-resource-share-associations, list-resources, list-principals, list-resource-types, get-resource-policies, promote-resource-share-created-from-policy, enable-sharing-with-aws-organization |
| Invitations | [`invitations.md`](invitations.md) | accept-resource-share-invitation, reject-resource-share-invitation, get-resource-share-invitations, list-pending-invitation-resources |
| Permissions | [`permissions.md`](permissions.md) | create-permission, create-permission-version, delete-permission, delete-permission-version, get-permission, list-permissions, list-permission-versions, list-permission-associations, list-resource-share-permissions, associate-resource-share-permission, disassociate-resource-share-permission, replace-permission-associations, list-replace-permission-associations-work, set-default-permission-version, promote-permission-created-from-policy |
| Organizations & Tags | [`organizations-tags.md`](organizations-tags.md) | tag-resource, untag-resource, list-source-associations |
