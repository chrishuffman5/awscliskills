# AWS CLI v2 — CodeArtifact

## Overview

Complete reference for all `aws codeartifact` subcommands in AWS CLI v2. Covers domain management, repository management, package operations, package version operations, package groups, authorization tokens, and tagging.

## Quick Reference — Common Workflows

### Create a domain
```bash
aws codeartifact create-domain --domain my-domain \
  --tags key=Environment,value=Production
```

### Create a repository
```bash
aws codeartifact create-repository --domain my-domain \
  --repository my-repo --description "My package repository"
```

### Associate an external connection (e.g., npmjs)
```bash
aws codeartifact associate-external-connection --domain my-domain \
  --repository my-repo --external-connection public:npmjs
```

### Configure npm/pip to use CodeArtifact
```bash
aws codeartifact login --tool npm --domain my-domain \
  --repository my-repo
```

### Get an authorization token
```bash
aws codeartifact get-authorization-token --domain my-domain \
  --query authorizationToken --output text
```

### List packages in a repository
```bash
aws codeartifact list-packages --domain my-domain \
  --repository my-repo --format npm
```

### Copy package versions between repositories
```bash
aws codeartifact copy-package-versions --domain my-domain \
  --source-repository upstream-repo --destination-repository prod-repo \
  --format npm --package my-package --versions '["1.0.0","1.1.0"]'
```

### Create a package group
```bash
aws codeartifact create-package-group --domain my-domain \
  --package-group "npm//my-scope/*"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Domains | [`domains.md`](domains.md) | create-domain, delete-domain, describe-domain, list-domains, get-domain-permissions-policy, put-domain-permissions-policy, delete-domain-permissions-policy |
| Repositories | [`repositories.md`](repositories.md) | create-repository, delete-repository, describe-repository, list-repositories, list-repositories-in-domain, update-repository, get-repository-endpoint, get-repository-permissions-policy, put-repository-permissions-policy, delete-repository-permissions-policy, associate-external-connection, disassociate-external-connection, login |
| Packages | [`packages.md`](packages.md) | describe-package, list-packages, delete-package, get-associated-package-group, put-package-origin-configuration |
| Package Versions | [`package-versions.md`](package-versions.md) | describe-package-version, list-package-versions, list-package-version-assets, list-package-version-dependencies, get-package-version-readme, get-package-version-asset, copy-package-versions, delete-package-versions, dispose-package-versions, update-package-versions-status, publish-package-version, get-authorization-token |
| Package Groups | [`package-groups.md`](package-groups.md) | create-package-group, delete-package-group, describe-package-group, list-package-groups, update-package-group, update-package-group-origin-configuration, list-allowed-repositories-for-group, list-associated-packages, list-sub-package-groups |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
