# AWS CLI v2 — API Gateway Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/apigateway/ and https://docs.aws.amazon.com/cli/latest/reference/apigatewayv2/

---

## Quick Reference — `aws apigateway` (REST APIs)

| Command | Category | Description |
|---------|----------|-------------|
| `create-rest-api` | REST API | Create a new REST API |
| `delete-rest-api` | REST API | Delete a REST API |
| `get-rest-api` | REST API | Get info about a REST API |
| `get-rest-apis` | REST API | List all REST APIs |
| `import-rest-api` | REST API | Import a REST API from Swagger/OpenAPI |
| `put-rest-api` | REST API | Replace a REST API definition |
| `update-rest-api` | REST API | Update REST API properties |
| `create-resource` | Resource | Create a child resource |
| `delete-resource` | Resource | Delete a resource |
| `get-resource` | Resource | Get info about a resource |
| `get-resources` | Resource | List all resources in a REST API |
| `put-method` | Method | Add a method to a resource |
| `get-method` | Method | Get info about a method |
| `delete-method` | Method | Delete a method |
| `put-method-response` | Method | Add a method response |
| `get-method-response` | Method | Get a method response |
| `delete-method-response` | Method | Delete a method response |
| `put-integration` | Method | Add an integration to a method |
| `get-integration` | Method | Get an integration |
| `delete-integration` | Method | Delete an integration |
| `put-integration-response` | Method | Add an integration response |
| `get-integration-response` | Method | Get an integration response |
| `delete-integration-response` | Method | Delete an integration response |
| `create-deployment` | Stage | Create a deployment |
| `delete-deployment` | Stage | Delete a deployment |
| `get-deployment` | Stage | Get info about a deployment |
| `get-deployments` | Stage | List deployments |
| `create-stage` | Stage | Create a stage |
| `delete-stage` | Stage | Delete a stage |
| `get-stage` | Stage | Get info about a stage |
| `get-stages` | Stage | List stages for a REST API |
| `update-stage` | Stage | Update stage configuration |
| `flush-stage-cache` | Stage | Flush the stage cache |
| `flush-stage-authorizers-cache` | Stage | Flush all authorizer caches in a stage |
| `create-authorizer` | Authorizer | Create an authorizer |
| `delete-authorizer` | Authorizer | Delete an authorizer |
| `get-authorizer` | Authorizer | Get info about an authorizer |
| `get-authorizers` | Authorizer | List authorizers |
| `update-authorizer` | Authorizer | Update an authorizer |
| `create-api-key` | API Key | Create an API key |
| `delete-api-key` | API Key | Delete an API key |
| `get-api-key` | API Key | Get info about an API key |
| `get-api-keys` | API Key | List API keys |
| `update-api-key` | API Key | Update an API key |
| `create-usage-plan` | Usage Plan | Create a usage plan |
| `delete-usage-plan` | Usage Plan | Delete a usage plan |
| `get-usage-plan` | Usage Plan | Get info about a usage plan |
| `get-usage-plans` | Usage Plan | List usage plans |
| `update-usage-plan` | Usage Plan | Update a usage plan |
| `create-usage-plan-key` | Usage Plan | Add an API key to a usage plan |
| `delete-usage-plan-key` | Usage Plan | Remove an API key from a usage plan |
| `get-usage-plan-key` | Usage Plan | Get a usage plan key |
| `get-usage-plan-keys` | Usage Plan | List keys in a usage plan |
| `get-usage` | Usage Plan | Get usage data for a usage plan |
| `create-model` | Model | Create a model |
| `delete-model` | Model | Delete a model |
| `get-model` | Model | Get info about a model |
| `get-models` | Model | List models |
| `update-model` | Model | Update a model |
| `create-domain-name` | Domain Name | Create a custom domain name |
| `delete-domain-name` | Domain Name | Delete a custom domain name |
| `get-domain-name` | Domain Name | Get info about a domain name |
| `get-domain-names` | Domain Name | List custom domain names |
| `update-domain-name` | Domain Name | Update a domain name |
| `create-base-path-mapping` | Domain Name | Create a base path mapping |
| `delete-base-path-mapping` | Domain Name | Delete a base path mapping |
| `get-base-path-mapping` | Domain Name | Get a base path mapping |
| `get-base-path-mappings` | Domain Name | List base path mappings |
| `update-base-path-mapping` | Domain Name | Update a base path mapping |
| `create-vpc-link` | VPC Link | Create a VPC link |
| `delete-vpc-link` | VPC Link | Delete a VPC link |
| `get-vpc-link` | VPC Link | Get info about a VPC link |
| `get-vpc-links` | VPC Link | List VPC links |
| `update-vpc-link` | VPC Link | Update a VPC link |
| `test-invoke-method` | Testing | Test invoke a method |
| `get-export` | Export | Export a REST API to a file |
| `get-sdk` | SDK | Generate an SDK for a REST API |
| `get-account` | Account | Get account-level API Gateway settings |
| `update-account` | Account | Update account-level settings |
| `get-gateway-responses` | Gateway Response | List gateway responses |
| `get-gateway-response` | Gateway Response | Get a gateway response |
| `put-gateway-response` | Gateway Response | Set a gateway response |
| `update-gateway-response` | Gateway Response | Update a gateway response |
| `delete-gateway-response` | Gateway Response | Delete a gateway response |

## Quick Reference — `aws apigatewayv2` (HTTP & WebSocket APIs)

| Command | Category | Description |
|---------|----------|-------------|
| `create-api` | API | Create an HTTP or WebSocket API |
| `delete-api` | API | Delete an API |
| `get-api` | API | Get info about an API |
| `get-apis` | API | List APIs |
| `update-api` | API | Update an API |
| `reimport-api` | API | Reimport an API from OpenAPI |
| `create-route` | Route | Create a route |
| `delete-route` | Route | Delete a route |
| `get-route` | Route | Get info about a route |
| `get-routes` | Route | List routes |
| `update-route` | Route | Update a route |
| `create-route-response` | Route | Create a route response |
| `delete-route-response` | Route | Delete a route response |
| `get-route-response` | Route | Get a route response |
| `get-route-responses` | Route | List route responses |
| `update-route-response` | Route | Update a route response |
| `create-integration` | Integration | Create an integration |
| `delete-integration` | Integration | Delete an integration |
| `get-integration` | Integration | Get info about an integration |
| `get-integrations` | Integration | List integrations |
| `update-integration` | Integration | Update an integration |
| `create-integration-response` | Integration | Create an integration response |
| `delete-integration-response` | Integration | Delete an integration response |
| `get-integration-response` | Integration | Get an integration response |
| `get-integration-responses` | Integration | List integration responses |
| `update-integration-response` | Integration | Update an integration response |
| `create-stage` | Stage | Create a stage |
| `delete-stage` | Stage | Delete a stage |
| `get-stage` | Stage | Get info about a stage |
| `get-stages` | Stage | List stages |
| `update-stage` | Stage | Update a stage |
| `create-deployment` | Deployment | Create a deployment |
| `delete-deployment` | Deployment | Delete a deployment |
| `get-deployment` | Deployment | Get info about a deployment |
| `get-deployments` | Deployment | List deployments |
| `create-authorizer` | Authorizer | Create an authorizer |
| `delete-authorizer` | Authorizer | Delete an authorizer |
| `get-authorizer` | Authorizer | Get info about an authorizer |
| `get-authorizers` | Authorizer | List authorizers |
| `update-authorizer` | Authorizer | Update an authorizer |
| `create-api-mapping` | Domain | Create an API mapping |
| `delete-api-mapping` | Domain | Delete an API mapping |
| `get-api-mapping` | Domain | Get an API mapping |
| `get-api-mappings` | Domain | List API mappings |
| `update-api-mapping` | Domain | Update an API mapping |
| `create-domain-name` | Domain | Create a domain name |
| `delete-domain-name` | Domain | Delete a domain name |
| `get-domain-name` | Domain | Get info about a domain name |
| `get-domain-names` | Domain | List domain names |
| `update-domain-name` | Domain | Update a domain name |
| `create-vpc-link` | VPC Link | Create a VPC link |
| `delete-vpc-link` | VPC Link | Delete a VPC link |
| `get-vpc-link` | VPC Link | Get info about a VPC link |
| `get-vpc-links` | VPC Link | List VPC links |
| `update-vpc-link` | VPC Link | Update a VPC link |
| `export-api` | Export | Export an API to OpenAPI |
| `tag-resource` | Tags | Tag a resource |
| `untag-resource` | Tags | Untag a resource |
| `get-tags` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws apigateway` and `aws apigatewayv2` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### REST API Endpoint Types
| Type | Description |
|------|-------------|
| `EDGE` | Edge-optimized (CloudFront distribution) |
| `REGIONAL` | Regional endpoint |
| `PRIVATE` | Private endpoint accessible only from VPC |

### Integration Types (REST API)
| Type | Description |
|------|-------------|
| `HTTP` | HTTP integration (custom HTTP endpoint) |
| `HTTP_PROXY` | HTTP proxy integration |
| `AWS` | AWS service integration |
| `AWS_PROXY` | Lambda proxy integration |
| `MOCK` | Mock integration |

### Authorization Types
| Type | Description |
|------|-------------|
| `NONE` | No authorization |
| `AWS_IAM` | IAM authorization |
| `CUSTOM` | Custom authorizer (Lambda) |
| `COGNITO_USER_POOLS` | Amazon Cognito user pool authorizer |

### HTTP API Protocol Types (v2)
| Type | Description |
|------|-------------|
| `HTTP` | HTTP API |
| `WEBSOCKET` | WebSocket API |

### Stage Variables
Stage variables are name-value pairs available in `$stageVariables` context. Useful for parameterizing integrations across stages.

### Patch Operations (update commands)
REST API update commands use JSON Patch operations:
```json
[
    {
        "op": "replace|add|remove|copy|move|test",
        "path": "/propertyName",
        "value": "newValue"
    }
]
```
