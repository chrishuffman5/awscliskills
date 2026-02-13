# AWS CLI v2 — Service Catalog

## Overview

Complete reference for all `aws servicecatalog` subcommands in AWS CLI v2. Covers portfolio management, product lifecycle, provisioned products, provisioning artifacts, constraints, service actions, principals, tag options, budgets, and AWS Organizations integration.

## Quick Reference — Common Workflows

### Create a portfolio
```bash
aws servicecatalog create-portfolio --display-name "My Portfolio" \
  --provider-name "IT Team" \
  --description "Approved infrastructure products"
```

### Create a product
```bash
aws servicecatalog create-product --name "EC2 Instance" \
  --owner "IT Team" --product-type CLOUD_FORMATION_TEMPLATE \
  --provisioning-artifact-parameters '{"Name":"v1","Info":{"LoadTemplateFromURL":"https://s3.amazonaws.com/bucket/template.yaml"},"Type":"CLOUD_FORMATION_TEMPLATE"}'
```

### Associate a product with a portfolio
```bash
aws servicecatalog associate-product-with-portfolio \
  --product-id prod-abc123 --portfolio-id port-abc123
```

### Provision a product
```bash
aws servicecatalog provision-product --product-id prod-abc123 \
  --provisioning-artifact-id pa-abc123 \
  --provisioned-product-name "my-instance" \
  --provisioning-parameters Key=InstanceType,Value=t3.micro
```

### Update a provisioned product
```bash
aws servicecatalog update-provisioned-product \
  --provisioned-product-name "my-instance" \
  --provisioning-artifact-id pa-def456 \
  --provisioning-parameters Key=InstanceType,Value=t3.large
```

### Terminate a provisioned product
```bash
aws servicecatalog terminate-provisioned-product \
  --provisioned-product-name "my-instance"
```

### Share a portfolio with another account
```bash
aws servicecatalog create-portfolio-share \
  --portfolio-id port-abc123 --account-id 123456789012
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Portfolios | [`portfolios.md`](portfolios.md) | create-portfolio, delete-portfolio, describe-portfolio, update-portfolio, list-portfolios, list-accepted-portfolio-shares, accept-portfolio-share, reject-portfolio-share, create-portfolio-share, delete-portfolio-share, describe-portfolio-share-status, describe-portfolio-shares, list-portfolio-access, list-organization-portfolio-access, update-portfolio-share |
| Products | [`products.md`](products.md) | create-product, delete-product, describe-product, describe-product-as-admin, describe-product-view, update-product, list-portfolios-for-product, associate-product-with-portfolio, disassociate-product-from-portfolio, copy-product, describe-copy-product-status, search-products, search-products-as-admin |
| Provisioning Artifacts | [`provisioning-artifacts.md`](provisioning-artifacts.md) | create-provisioning-artifact, delete-provisioning-artifact, describe-provisioning-artifact, update-provisioning-artifact, list-provisioning-artifacts, describe-provisioning-parameters |
| Provisioned Products | [`provisioned-products.md`](provisioned-products.md) | provision-product, terminate-provisioned-product, update-provisioned-product, update-provisioned-product-properties, describe-provisioned-product, search-provisioned-products, scan-provisioned-products, get-provisioned-product-outputs, import-as-provisioned-product, list-record-history, describe-record, list-stack-instances-for-provisioned-product |
| Provisioned Product Plans | [`provisioned-product-plans.md`](provisioned-product-plans.md) | create-provisioned-product-plan, delete-provisioned-product-plan, describe-provisioned-product-plan, execute-provisioned-product-plan, list-provisioned-product-plans |
| Constraints | [`constraints.md`](constraints.md) | create-constraint, delete-constraint, describe-constraint, update-constraint, list-constraints-for-portfolio, list-launch-paths |
| Service Actions | [`service-actions.md`](service-actions.md) | create-service-action, delete-service-action, describe-service-action, update-service-action, list-service-actions, associate-service-action-with-provisioning-artifact, disassociate-service-action-from-provisioning-artifact, batch-associate-service-action-with-provisioning-artifact, batch-disassociate-service-action-from-provisioning-artifact, list-service-actions-for-provisioning-artifact, describe-service-action-execution-parameters, execute-provisioned-product-service-action |
| Principals | [`principals.md`](principals.md) | associate-principal-with-portfolio, disassociate-principal-from-portfolio, list-principals-for-portfolio |
| Tag Options | [`tag-options.md`](tag-options.md) | create-tag-option, delete-tag-option, describe-tag-option, update-tag-option, list-tag-options, associate-tag-option-with-resource, disassociate-tag-option-from-resource, list-resources-for-tag-option |
| Budgets | [`budgets.md`](budgets.md) | associate-budget-with-resource, disassociate-budget-from-resource, list-budgets-for-resource |
| Organizations | [`organizations.md`](organizations.md) | enable-aws-organizations-access, disable-aws-organizations-access, get-aws-organizations-access-status |
| Notifications | [`notifications.md`](notifications.md) | notify-provision-product-engine-workflow-result, notify-terminate-provisioned-product-engine-workflow-result, notify-update-provisioned-product-engine-workflow-result |
