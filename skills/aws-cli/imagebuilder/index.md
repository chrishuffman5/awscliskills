# AWS CLI v2 -- EC2 Image Builder Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/imagebuilder/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-image-pipeline` | Pipeline | Create an image pipeline |
| `get-image-pipeline` | Pipeline | Get image pipeline details |
| `list-image-pipelines` | Pipeline | List all image pipelines |
| `update-image-pipeline` | Pipeline | Update an image pipeline |
| `delete-image-pipeline` | Pipeline | Delete an image pipeline |
| `start-image-pipeline-execution` | Pipeline | Start a pipeline execution |
| `list-image-pipeline-images` | Pipeline | List images produced by a pipeline |
| `create-image-recipe` | Image Recipe | Create an image recipe |
| `get-image-recipe` | Image Recipe | Get image recipe details |
| `list-image-recipes` | Image Recipe | List all image recipes |
| `get-image-recipe-policy` | Image Recipe | Get the image recipe policy |
| `put-image-recipe-policy` | Image Recipe | Set the image recipe policy |
| `delete-image-recipe` | Image Recipe | Delete an image recipe |
| `create-container-recipe` | Container Recipe | Create a container recipe |
| `get-container-recipe` | Container Recipe | Get container recipe details |
| `list-container-recipes` | Container Recipe | List all container recipes |
| `get-container-recipe-policy` | Container Recipe | Get the container recipe policy |
| `put-container-recipe-policy` | Container Recipe | Set the container recipe policy |
| `delete-container-recipe` | Container Recipe | Delete a container recipe |
| `create-component` | Component | Create a build or test component |
| `get-component` | Component | Get component details |
| `list-components` | Component | List all components |
| `import-component` | Component | Import a component from an S3 URI |
| `get-component-policy` | Component | Get the component policy |
| `put-component-policy` | Component | Set the component policy |
| `delete-component` | Component | Delete a component |
| `list-component-build-versions` | Component | List component build versions |
| `create-image` | Image | Create an image |
| `get-image` | Image | Get image details |
| `list-images` | Image | List all images |
| `list-image-build-versions` | Image | List image build versions |
| `get-image-policy` | Image | Get the image policy |
| `put-image-policy` | Image | Set the image policy |
| `delete-image` | Image | Delete an image |
| `cancel-image-creation` | Image | Cancel an in-progress image creation |
| `import-vm-image` | Image | Import a VM image |
| `list-image-scan-findings` | Image Scanning | List image scan findings |
| `list-image-scan-finding-aggregations` | Image Scanning | List aggregated scan findings |
| `create-infrastructure-configuration` | Infrastructure | Create an infrastructure configuration |
| `get-infrastructure-configuration` | Infrastructure | Get infrastructure configuration details |
| `list-infrastructure-configurations` | Infrastructure | List all infrastructure configurations |
| `update-infrastructure-configuration` | Infrastructure | Update an infrastructure configuration |
| `delete-infrastructure-configuration` | Infrastructure | Delete an infrastructure configuration |
| `create-distribution-configuration` | Distribution | Create a distribution configuration |
| `get-distribution-configuration` | Distribution | Get distribution configuration details |
| `list-distribution-configurations` | Distribution | List all distribution configurations |
| `update-distribution-configuration` | Distribution | Update a distribution configuration |
| `delete-distribution-configuration` | Distribution | Delete a distribution configuration |
| `create-lifecycle-policy` | Lifecycle | Create a lifecycle policy |
| `get-lifecycle-policy` | Lifecycle | Get lifecycle policy details |
| `list-lifecycle-policies` | Lifecycle | List all lifecycle policies |
| `update-lifecycle-policy` | Lifecycle | Update a lifecycle policy |
| `delete-lifecycle-policy` | Lifecycle | Delete a lifecycle policy |
| `list-lifecycle-executions` | Lifecycle | List lifecycle executions |
| `list-lifecycle-execution-resources` | Lifecycle | List resources affected by a lifecycle execution |
| `create-workflow` | Workflow | Create a workflow |
| `get-workflow` | Workflow | Get workflow details |
| `list-workflows` | Workflow | List all workflows |
| `get-workflow-execution` | Workflow | Get workflow execution details |
| `list-workflow-executions` | Workflow | List workflow executions |
| `get-workflow-step-execution` | Workflow | Get workflow step execution details |
| `list-workflow-step-executions` | Workflow | List workflow step executions |
| `list-workflow-build-versions` | Workflow | List workflow build versions |
| `delete-workflow` | Workflow | Delete a workflow |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws imagebuilder` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
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

### Image Build Statuses
| Status | Description |
|--------|-------------|
| `PENDING` | Image build is pending |
| `CREATING` | Image is being created |
| `BUILDING` | Image is being built |
| `TESTING` | Image is being tested |
| `DISTRIBUTING` | Image is being distributed |
| `INTEGRATING` | Image is being integrated |
| `AVAILABLE` | Image is available |
| `CANCELLED` | Image build was cancelled |
| `FAILED` | Image build failed |
| `DEPRECATED` | Image has been deprecated |
| `DELETED` | Image has been deleted |
| `DISABLED` | Image has been disabled |

### Pipeline Statuses
| Status | Description |
|--------|-------------|
| `DISABLED` | Pipeline is disabled |
| `ENABLED` | Pipeline is enabled |

### Platforms
| Platform | Description |
|----------|-------------|
| `Windows` | Windows-based images |
| `Linux` | Linux-based images |

### Component Types
| Type | Description |
|------|-------------|
| `BUILD` | Component runs during the build phase |
| `TEST` | Component runs during the test phase |

### Semantic Versioning
All resources use semantic versioning in the format `major.minor.patch` (e.g., `1.0.0`). Use `x.x.x` as a wildcard to match the latest version.

### ARN Format
```
arn:aws:imagebuilder:{region}:{account}:{resource-type}/{name}/{version}
```

### Pipeline Execution Start Conditions
| Condition | Description |
|-----------|-------------|
| `EXPRESSION_MATCH_ONLY` | Run on schedule only |
| `EXPRESSION_MATCH_AND_DEPENDENCY_UPDATES_AVAILABLE` | Run on schedule only if dependency updates are available |
