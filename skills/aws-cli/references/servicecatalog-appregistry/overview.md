# AWS CLI v2 — Service Catalog AppRegistry

## Overview

Complete reference for all `aws servicecatalog-appregistry` subcommands in AWS CLI v2. Covers application management, attribute group management, resource and attribute group associations, configuration, tagging, and resource synchronization. Service Catalog AppRegistry enables organizations to understand the application context of their AWS resources by providing a repository of applications and their metadata.

## Quick Reference — Common Workflows

### Create an application and attribute group
```bash
aws servicecatalog-appregistry create-application \
    --name "MyWebApp" \
    --description "Production web application"

aws servicecatalog-appregistry create-attribute-group \
    --name "MyAppAttributes" \
    --attributes '{"Environment":"Production","CostCenter":"12345","Team":"Platform"}' \
    --description "Attributes for production web app"
```

### Associate an attribute group with an application
```bash
aws servicecatalog-appregistry associate-attribute-group \
    --application "MyWebApp" \
    --attribute-group "MyAppAttributes"
```

### Associate a CloudFormation stack with an application
```bash
aws servicecatalog-appregistry associate-resource \
    --application "MyWebApp" \
    --resource-type CFN_STACK \
    --resource "arn:aws:cloudformation:us-east-1:123456789012:stack/my-stack/guid"
```

### List all resources for an application
```bash
aws servicecatalog-appregistry list-associated-resources \
    --application "MyWebApp" \
    --query 'resources[].{Name:name,ARN:arn,Type:resourceType}'
```

### Configure tag-based resource association
```bash
aws servicecatalog-appregistry put-configuration \
    --configuration '{"tagQueryConfiguration":{"tagKey":"awsApplication"}}'
```

### Tag an application
```bash
aws servicecatalog-appregistry tag-resource \
    --resource-arn "arn:aws:servicecatalog:us-east-1:123456789012:/applications/abc123" \
    --tags Environment=Production,Owner=PlatformTeam
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Applications | [`applications.md`](applications.md) | `create-application`, `get-application`, `list-applications`, `update-application`, `delete-application` |
| Attribute Groups | [`attribute-groups.md`](attribute-groups.md) | `create-attribute-group`, `get-attribute-group`, `list-attribute-groups`, `update-attribute-group`, `delete-attribute-group`, `list-attribute-groups-for-application` |
| Associations | [`associations.md`](associations.md) | `associate-attribute-group`, `disassociate-attribute-group`, `associate-resource`, `disassociate-resource`, `get-associated-resource`, `list-associated-attribute-groups`, `list-associated-resources`, `sync-resource` |
| Configuration & Tags | [`configuration-tags.md`](configuration-tags.md) | `get-configuration`, `put-configuration`, `tag-resource`, `untag-resource`, `list-tags-for-resource` |
