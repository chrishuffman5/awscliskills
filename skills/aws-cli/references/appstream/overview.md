# AWS CLI v2 — AppStream 2.0

## Overview

Complete reference for all `aws appstream` subcommands in AWS CLI v2. Covers fleet management, stack configuration, image management, image builders, app blocks, applications, entitlements, directory configurations, and user management for Amazon AppStream 2.0 application streaming.

## Quick Reference — Common Workflows

### Create a fleet
```bash
aws appstream create-fleet --name my-fleet \
  --instance-type stream.standard.medium \
  --image-name AppStream-WinServer2019-01-2024 \
  --fleet-type ALWAYS_ON \
  --compute-capacity DesiredInstances=2
```

### Create a stack and associate fleet
```bash
aws appstream create-stack --name my-stack \
  --storage-connectors '[{"ConnectorType":"HOMEFOLDERS"}]'
aws appstream associate-fleet --fleet-name my-fleet --stack-name my-stack
```

### Start a fleet
```bash
aws appstream start-fleet --name my-fleet
aws appstream wait fleet-started --name my-fleet
```

### Create a streaming URL
```bash
aws appstream create-streaming-url --stack-name my-stack \
  --fleet-name my-fleet --user-id user@example.com \
  --validity 3600
```

### Create an image builder
```bash
aws appstream create-image-builder --name my-builder \
  --image-name AppStream-WinServer2019-01-2024 \
  --instance-type stream.standard.medium
aws appstream start-image-builder --name my-builder
```

### Manage users
```bash
aws appstream create-user --user-name user@example.com \
  --authentication-type USERPOOL --first-name John --last-name Doe
aws appstream batch-associate-user-stack \
  --user-stack-associations '[{"StackName":"my-stack","UserName":"user@example.com","AuthenticationType":"USERPOOL","SendEmailNotification":true}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Fleets | [`fleets.md`](fleets.md) | create-fleet, delete-fleet, describe-fleets, update-fleet, start-fleet, stop-fleet, associate-fleet, disassociate-fleet, list-associated-fleets, list-associated-stacks |
| Stacks | [`stacks.md`](stacks.md) | create-stack, delete-stack, describe-stacks, update-stack, create-streaming-url, describe-sessions, expire-session |
| Images | [`images.md`](images.md) | describe-images, delete-image, copy-image, describe-image-permissions, update-image-permissions, delete-image-permissions, create-updated-image |
| Image Builders | [`image-builders.md`](image-builders.md) | create-image-builder, delete-image-builder, describe-image-builders, start-image-builder, stop-image-builder, create-image-builder-streaming-url |
| App Blocks | [`app-blocks.md`](app-blocks.md) | create-app-block, delete-app-block, describe-app-blocks, create-app-block-builder, delete-app-block-builder, describe-app-block-builders, update-app-block-builder, start-app-block-builder, stop-app-block-builder |
| Applications | [`applications.md`](applications.md) | create-application, delete-application, describe-applications, update-application, associate-application-fleet, disassociate-application-fleet, describe-application-fleet-associations |
| Entitlements | [`entitlements.md`](entitlements.md) | create-entitlement, delete-entitlement, describe-entitlements, update-entitlement, list-entitled-applications |
| Directory Configs | [`directory-configs.md`](directory-configs.md) | create-directory-config, delete-directory-config, describe-directory-configs, update-directory-config |
| Users | [`users.md`](users.md) | create-user, delete-user, describe-users, disable-user, enable-user, batch-associate-user-stack, batch-disassociate-user-stack, describe-user-stack-associations |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait: fleet-started, fleet-stopped |
