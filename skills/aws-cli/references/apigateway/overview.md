# AWS CLI v2 — API Gateway (REST APIs + HTTP/WebSocket APIs)

## Overview

Complete reference for `aws apigateway` (REST APIs) and `aws apigatewayv2` (HTTP APIs, WebSocket APIs) subcommands in AWS CLI v2. Covers REST API management, resource/method configuration, stages, deployments, authorizers, API keys, usage plans, models, domain names, VPC links, and the v2 HTTP/WebSocket API equivalents.

## Quick Reference — Common Workflows

### Create a REST API
```bash
aws apigateway create-rest-api --name my-api \
  --description "My REST API" \
  --endpoint-configuration types=REGIONAL
```

### Create a resource and method
```bash
# Get the root resource ID
ROOT_ID=$(aws apigateway get-resources --rest-api-id abc123 \
  --query 'items[?path==`/`].id' --output text)

# Create /users resource
aws apigateway create-resource --rest-api-id abc123 \
  --parent-id "$ROOT_ID" --path-part users

# Add GET method
aws apigateway put-method --rest-api-id abc123 \
  --resource-id xyz789 --http-method GET \
  --authorization-type NONE
```

### Set up Lambda integration
```bash
aws apigateway put-integration --rest-api-id abc123 \
  --resource-id xyz789 --http-method GET \
  --type AWS_PROXY \
  --integration-http-method POST \
  --uri "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:123456789012:function:my-func/invocations"
```

### Deploy to a stage
```bash
aws apigateway create-deployment --rest-api-id abc123 --stage-name prod \
  --description "Production deployment"
```

### Create an HTTP API (v2)
```bash
aws apigatewayv2 create-api --name my-http-api \
  --protocol-type HTTP \
  --target "arn:aws:lambda:us-east-1:123456789012:function:my-func"
```

### Create a custom domain name
```bash
aws apigateway create-domain-name --domain-name api.example.com \
  --regional-certificate-arn arn:aws:acm:us-east-1:123456789012:certificate/abc123 \
  --endpoint-configuration types=REGIONAL
```

### Create an API key and usage plan
```bash
aws apigateway create-api-key --name my-key --enabled
aws apigateway create-usage-plan --name my-plan \
  --api-stages apiId=abc123,stage=prod \
  --throttle burstLimit=100,rateLimit=50
aws apigateway create-usage-plan-key --usage-plan-id plan123 \
  --key-id key123 --key-type API_KEY
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| REST APIs | [`rest-apis.md`](rest-apis.md) | create-rest-api, delete-rest-api, get-rest-api, get-rest-apis, import-rest-api, put-rest-api, update-rest-api |
| Resources | [`resources.md`](resources.md) | create-resource, delete-resource, get-resource, get-resources |
| Methods | [`methods.md`](methods.md) | put-method, get-method, delete-method, put-method-response, get-method-response, delete-method-response, put-integration, get-integration, delete-integration, put-integration-response, get-integration-response, delete-integration-response, test-invoke-method |
| Stages | [`stages.md`](stages.md) | create-stage, delete-stage, get-stage, get-stages, update-stage, create-deployment, delete-deployment, get-deployment, get-deployments, flush-stage-cache, flush-stage-authorizers-cache |
| Authorizers | [`authorizers.md`](authorizers.md) | create-authorizer, delete-authorizer, get-authorizer, get-authorizers, update-authorizer |
| API Keys | [`api-keys.md`](api-keys.md) | create-api-key, delete-api-key, get-api-key, get-api-keys, update-api-key, create-usage-plan, delete-usage-plan, get-usage-plan, get-usage-plans, update-usage-plan, create-usage-plan-key, delete-usage-plan-key, get-usage-plan-key, get-usage-plan-keys, get-usage |
| Models | [`models.md`](models.md) | create-model, delete-model, get-model, get-models, update-model |
| Domain Names | [`domain-names.md`](domain-names.md) | create-domain-name, delete-domain-name, get-domain-name, get-domain-names, update-domain-name, create-base-path-mapping, delete-base-path-mapping, get-base-path-mapping, get-base-path-mappings, update-base-path-mapping |
| VPC Links | [`vpc-links.md`](vpc-links.md) | create-vpc-link, delete-vpc-link, get-vpc-link, get-vpc-links, update-vpc-link |
| HTTP APIs (v2) | [`http-apis.md`](http-apis.md) | create-api, delete-api, get-api, get-apis, update-api, create-route, delete-route, get-route, get-routes, update-route, create-integration, delete-integration, get-integration, get-integrations, update-integration, create-stage, delete-stage, get-stage, get-stages, update-stage, create-authorizer, delete-authorizer, get-authorizer, get-authorizers, update-authorizer, create-deployment, delete-deployment, get-deployment, get-deployments |
