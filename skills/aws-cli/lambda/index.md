# AWS CLI v2 -- Lambda (Serverless Compute) Complete Command Reference

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/lambda/

---

## All Lambda Subcommands (Quick Reference)

| Command | Category | Description |
|---------|----------|-------------|
| `add-layer-version-permission` | Layers | Add permission to a layer version |
| `add-permission` | Permissions | Add permission to a function's resource-based policy |
| `create-alias` | Aliases | Create a function alias |
| `create-code-signing-config` | Code Signing | Create a code signing configuration |
| `create-event-source-mapping` | Event Sources | Create an event source mapping |
| `create-function` | Functions | Create a Lambda function |
| `create-function-url-config` | Function URLs | Create a function URL configuration |
| `delete-alias` | Aliases | Delete a function alias |
| `delete-code-signing-config` | Code Signing | Delete a code signing configuration |
| `delete-event-source-mapping` | Event Sources | Delete an event source mapping |
| `delete-function` | Functions | Delete a Lambda function |
| `delete-function-code-signing-config` | Code Signing | Remove code signing config from a function |
| `delete-function-concurrency` | Concurrency | Remove reserved concurrency setting |
| `delete-function-event-invoke-config` | Functions | Delete async invocation configuration |
| `delete-function-url-config` | Function URLs | Delete a function URL configuration |
| `delete-layer-version` | Layers | Delete a layer version |
| `delete-provisioned-concurrency-config` | Concurrency | Delete provisioned concurrency config |
| `get-account-settings` | Account | Get Lambda account settings and limits |
| `get-alias` | Aliases | Get alias details |
| `get-code-signing-config` | Code Signing | Get code signing configuration details |
| `get-event-source-mapping` | Event Sources | Get event source mapping details |
| `get-function` | Functions | Get function details (config + code location + tags) |
| `get-function-code-signing-config` | Code Signing | Get function's code signing config |
| `get-function-concurrency` | Concurrency | Get reserved concurrency setting |
| `get-function-configuration` | Functions | Get function configuration only |
| `get-function-event-invoke-config` | Functions | Get async invocation configuration |
| `get-function-recursion-config` | Functions | Get function recursion configuration |
| `get-function-url-config` | Function URLs | Get function URL configuration |
| `get-layer-version` | Layers | Get layer version details |
| `get-layer-version-by-arn` | Layers | Get layer version by ARN |
| `get-layer-version-policy` | Layers | Get layer version resource policy |
| `get-policy` | Permissions | Get function resource-based policy |
| `get-provisioned-concurrency-config` | Concurrency | Get provisioned concurrency config |
| `get-runtime-management-config` | Runtime | Get runtime management configuration |
| `invoke` | Invocation | Invoke a Lambda function |
| `list-aliases` | Aliases | List function aliases |
| `list-code-signing-configs` | Code Signing | List code signing configurations |
| `list-event-source-mappings` | Event Sources | List event source mappings |
| `list-function-event-invoke-configs` | Functions | List async invocation configurations |
| `list-function-url-configs` | Function URLs | List function URL configurations |
| `list-functions` | Functions | List Lambda functions |
| `list-functions-by-code-signing-config` | Code Signing | List functions using a signing config |
| `list-layer-versions` | Layers | List versions of a layer |
| `list-layers` | Layers | List Lambda layers |
| `list-provisioned-concurrency-configs` | Concurrency | List provisioned concurrency configs |
| `list-tags` | Tags | List resource tags |
| `list-versions-by-function` | Versions | List function versions |
| `publish-layer-version` | Layers | Publish a layer version |
| `publish-version` | Versions | Publish a function version |
| `put-function-code-signing-config` | Code Signing | Set function code signing config |
| `put-function-concurrency` | Concurrency | Set reserved concurrency |
| `put-function-event-invoke-config` | Functions | Set async invocation configuration |
| `put-function-recursion-config` | Functions | Set function recursion configuration |
| `put-provisioned-concurrency-config` | Concurrency | Set provisioned concurrency |
| `put-runtime-management-config` | Runtime | Set runtime management configuration |
| `remove-layer-version-permission` | Layers | Remove permission from layer version |
| `remove-permission` | Permissions | Remove permission from function policy |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `update-alias` | Aliases | Update a function alias |
| `update-code-signing-config` | Code Signing | Update code signing configuration |
| `update-event-source-mapping` | Event Sources | Update event source mapping |
| `update-function-code` | Functions | Update function code |
| `update-function-configuration` | Functions | Update function configuration |
| `update-function-event-invoke-config` | Functions | Update async invocation configuration |
| `update-function-url-config` | Function URLs | Update function URL configuration |

---

---

# Global Options Reference

These options are available on all `aws lambda` commands:

| Option | Type | Description |
|--------|------|-------------|
| `--debug` | boolean | Enable debug logging |
| `--endpoint-url` | string | Override default endpoint URL |
| `--no-verify-ssl` | boolean | Disable SSL certificate verification |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query to filter output |
| `--profile` | string | Named AWS profile |
| `--region` | string | AWS region (e.g., `us-east-1`) |
| `--color` | string | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | Do not sign requests |
| `--ca-bundle` | string | CA certificate bundle path |
| `--cli-read-timeout` | integer | Socket read timeout in seconds (default 60) |
| `--cli-connect-timeout` | integer | Socket connect timeout in seconds (default 60) |
| `--cli-binary-format` | string | Format for binary blobs: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | Disable output paging |
| `--cli-auto-prompt` | boolean | Auto-prompt for parameters |
| `--no-cli-auto-prompt` | boolean | Disable auto-prompt |
| `--cli-input-json` | string | Read arguments from JSON string |
| `--cli-input-yaml` | string | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | Print skeleton without sending request: `input`, `output`, `yaml-input` |
