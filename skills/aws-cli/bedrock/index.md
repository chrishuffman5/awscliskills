# AWS CLI v2 -- Amazon Bedrock Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/bedrock/ , https://docs.aws.amazon.com/cli/latest/reference/bedrock-agent/ , https://docs.aws.amazon.com/cli/latest/reference/bedrock-agent-runtime/ , https://docs.aws.amazon.com/cli/latest/reference/bedrock-runtime/

---

## Quick Reference

### `aws bedrock` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `list-foundation-models` | Foundation Models | List available foundation models |
| `get-foundation-model` | Foundation Models | Get details about a foundation model |
| `list-foundation-model-agreement-offers` | Foundation Models | List agreement offers for a foundation model |
| `create-foundation-model-agreement` | Foundation Models | Create an agreement for a foundation model |
| `delete-foundation-model-agreement` | Foundation Models | Delete a foundation model agreement |
| `get-foundation-model-availability` | Foundation Models | Get availability info for a foundation model |
| `create-model-customization-job` | Custom Models | Create a fine-tuning or continued pre-training job |
| `get-model-customization-job` | Custom Models | Get details of a model customization job |
| `list-model-customization-jobs` | Custom Models | List model customization jobs |
| `stop-model-customization-job` | Custom Models | Stop a running model customization job |
| `create-custom-model` | Custom Models | Create a custom model |
| `get-custom-model` | Custom Models | Get details of a custom model |
| `list-custom-models` | Custom Models | List custom models |
| `delete-custom-model` | Custom Models | Delete a custom model |
| `create-custom-model-deployment` | Custom Models | Create a custom model deployment |
| `get-custom-model-deployment` | Custom Models | Get custom model deployment details |
| `list-custom-model-deployments` | Custom Models | List custom model deployments |
| `delete-custom-model-deployment` | Custom Models | Delete a custom model deployment |
| `create-model-import-job` | Model Import & Copy | Import a model from S3 |
| `get-model-import-job` | Model Import & Copy | Get details of a model import job |
| `list-model-import-jobs` | Model Import & Copy | List model import jobs |
| `get-imported-model` | Model Import & Copy | Get details of an imported model |
| `list-imported-models` | Model Import & Copy | List imported models |
| `delete-imported-model` | Model Import & Copy | Delete an imported model |
| `create-model-copy-job` | Model Import & Copy | Copy a model to another region |
| `get-model-copy-job` | Model Import & Copy | Get details of a model copy job |
| `list-model-copy-jobs` | Model Import & Copy | List model copy jobs |
| `create-provisioned-model-throughput` | Provisioned Throughput | Create dedicated throughput for a model |
| `get-provisioned-model-throughput` | Provisioned Throughput | Get provisioned throughput details |
| `list-provisioned-model-throughputs` | Provisioned Throughput | List provisioned throughputs |
| `update-provisioned-model-throughput` | Provisioned Throughput | Update a provisioned throughput |
| `delete-provisioned-model-throughput` | Provisioned Throughput | Delete a provisioned throughput |
| `create-guardrail` | Guardrails | Create a guardrail with content policies |
| `get-guardrail` | Guardrails | Get guardrail details |
| `list-guardrails` | Guardrails | List guardrails |
| `update-guardrail` | Guardrails | Update a guardrail |
| `delete-guardrail` | Guardrails | Delete a guardrail |
| `create-guardrail-version` | Guardrails | Create a versioned snapshot of a guardrail |
| `get-guardrail-policy` | Guardrails | Get the policy for a guardrail |
| `create-inference-profile` | Inference Profiles | Create an inference profile for cost tracking |
| `get-inference-profile` | Inference Profiles | Get inference profile details |
| `list-inference-profiles` | Inference Profiles | List inference profiles |
| `delete-inference-profile` | Inference Profiles | Delete an inference profile |
| `create-prompt-router` | Inference Profiles | Create a prompt router |
| `get-prompt-router` | Inference Profiles | Get prompt router details |
| `list-prompt-routers` | Inference Profiles | List prompt routers |
| `delete-prompt-router` | Inference Profiles | Delete a prompt router |
| `create-evaluation-job` | Evaluation Jobs | Create a model evaluation job |
| `get-evaluation-job` | Evaluation Jobs | Get evaluation job details |
| `list-evaluation-jobs` | Evaluation Jobs | List evaluation jobs |
| `stop-evaluation-job` | Evaluation Jobs | Stop an evaluation job |
| `batch-delete-evaluation-job` | Evaluation Jobs | Batch delete evaluation jobs |
| `create-model-invocation-job` | Invocation Jobs | Create a batch inference job |
| `get-model-invocation-job` | Invocation Jobs | Get batch inference job details |
| `list-model-invocation-jobs` | Invocation Jobs | List batch inference jobs |
| `stop-model-invocation-job` | Invocation Jobs | Stop a batch inference job |
| `create-marketplace-model-endpoint` | Marketplace | Create a marketplace model endpoint |
| `get-marketplace-model-endpoint` | Marketplace | Get marketplace endpoint details |
| `list-marketplace-model-endpoints` | Marketplace | List marketplace endpoints |
| `update-marketplace-model-endpoint` | Marketplace | Update a marketplace endpoint |
| `delete-marketplace-model-endpoint` | Marketplace | Delete a marketplace endpoint |
| `register-marketplace-model-endpoint` | Marketplace | Register an existing SageMaker endpoint |
| `deregister-marketplace-model-endpoint` | Marketplace | Deregister a marketplace endpoint |
| `create-automated-reasoning-policy` | Automated Reasoning | Create an automated reasoning policy |
| `get-automated-reasoning-policy` | Automated Reasoning | Get automated reasoning policy details |
| `list-automated-reasoning-policies` | Automated Reasoning | List automated reasoning policies |
| `delete-automated-reasoning-policy` | Automated Reasoning | Delete an automated reasoning policy |
| `create-automated-reasoning-policy-version` | Automated Reasoning | Create a version of a reasoning policy |
| `create-automated-reasoning-policy-test-case` | Automated Reasoning | Create a test case for a reasoning policy |
| `start-automated-reasoning-policy-build-workflow` | Automated Reasoning | Start building a reasoning policy |
| `cancel-automated-reasoning-policy-build-workflow` | Automated Reasoning | Cancel a reasoning policy build |
| `get-automated-reasoning-policy-build-workflow-status` | Automated Reasoning | Get build workflow status |
| `put-model-invocation-logging-configuration` | Logging | Configure model invocation logging |
| `get-model-invocation-logging-configuration` | Logging | Get model invocation logging config |
| `put-use-case-for-model-access` | Access | Set use case for model access |
| `tag-resource` | Tags | Add tags to a Bedrock resource |
| `untag-resource` | Tags | Remove tags from a Bedrock resource |
| `list-tags-for-resource` | Tags | List tags for a Bedrock resource |

### `aws bedrock-agent` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `create-agent` | Agents | Create a new agent |
| `get-agent` | Agents | Get agent details |
| `list-agents` | Agents | List all agents |
| `update-agent` | Agents | Update an agent |
| `delete-agent` | Agents | Delete an agent |
| `prepare-agent` | Agents | Prepare an agent for use |
| `create-agent-alias` | Agents | Create an alias for an agent |
| `get-agent-alias` | Agents | Get agent alias details |
| `list-agent-aliases` | Agents | List agent aliases |
| `update-agent-alias` | Agents | Update an agent alias |
| `delete-agent-alias` | Agents | Delete an agent alias |
| `get-agent-version` | Agents | Get agent version details |
| `list-agent-versions` | Agents | List agent versions |
| `delete-agent-version` | Agents | Delete an agent version |
| `create-agent-action-group` | Agent Action Groups | Create an action group for an agent |
| `get-agent-action-group` | Agent Action Groups | Get action group details |
| `list-agent-action-groups` | Agent Action Groups | List agent action groups |
| `update-agent-action-group` | Agent Action Groups | Update an action group |
| `delete-agent-action-group` | Agent Action Groups | Delete an action group |
| `associate-agent-knowledge-base` | Agent Knowledge Bases | Associate a knowledge base with an agent |
| `get-agent-knowledge-base` | Agent Knowledge Bases | Get agent knowledge base association |
| `list-agent-knowledge-bases` | Agent Knowledge Bases | List agent knowledge base associations |
| `update-agent-knowledge-base` | Agent Knowledge Bases | Update agent knowledge base association |
| `disassociate-agent-knowledge-base` | Agent Knowledge Bases | Remove a knowledge base from an agent |
| `associate-agent-collaborator` | Agent Knowledge Bases | Associate a collaborator with an agent |
| `get-agent-collaborator` | Agent Knowledge Bases | Get collaborator details |
| `list-agent-collaborators` | Agent Knowledge Bases | List agent collaborators |
| `update-agent-collaborator` | Agent Knowledge Bases | Update an agent collaborator |
| `disassociate-agent-collaborator` | Agent Knowledge Bases | Remove a collaborator from an agent |
| `create-knowledge-base` | Knowledge Bases | Create a knowledge base |
| `get-knowledge-base` | Knowledge Bases | Get knowledge base details |
| `list-knowledge-bases` | Knowledge Bases | List knowledge bases |
| `update-knowledge-base` | Knowledge Bases | Update a knowledge base |
| `delete-knowledge-base` | Knowledge Bases | Delete a knowledge base |
| `create-data-source` | Knowledge Bases | Create a data source for a knowledge base |
| `get-data-source` | Knowledge Bases | Get data source details |
| `list-data-sources` | Knowledge Bases | List data sources |
| `update-data-source` | Knowledge Bases | Update a data source |
| `delete-data-source` | Knowledge Bases | Delete a data source |
| `start-ingestion-job` | Knowledge Bases | Start ingesting data into a knowledge base |
| `get-ingestion-job` | Knowledge Bases | Get ingestion job details |
| `list-ingestion-jobs` | Knowledge Bases | List ingestion jobs |
| `stop-ingestion-job` | Knowledge Bases | Stop an ingestion job |
| `ingest-knowledge-base-documents` | Knowledge Bases | Ingest documents into a knowledge base |
| `get-knowledge-base-documents` | Knowledge Bases | Get knowledge base documents |
| `list-knowledge-base-documents` | Knowledge Bases | List knowledge base documents |
| `delete-knowledge-base-documents` | Knowledge Bases | Delete knowledge base documents |
| `create-prompt` | Prompts | Create a managed prompt |
| `get-prompt` | Prompts | Get prompt details |
| `list-prompts` | Prompts | List managed prompts |
| `update-prompt` | Prompts | Update a prompt |
| `delete-prompt` | Prompts | Delete a prompt |
| `create-prompt-version` | Prompts | Create a version of a prompt |
| `create-flow` | Flows | Create a flow |
| `get-flow` | Flows | Get flow details |
| `list-flows` | Flows | List flows |
| `update-flow` | Flows | Update a flow |
| `delete-flow` | Flows | Delete a flow |
| `prepare-flow` | Flows | Prepare a flow for execution |
| `validate-flow-definition` | Flows | Validate a flow definition |
| `create-flow-alias` | Flows | Create a flow alias |
| `get-flow-alias` | Flows | Get flow alias details |
| `list-flow-aliases` | Flows | List flow aliases |
| `update-flow-alias` | Flows | Update a flow alias |
| `delete-flow-alias` | Flows | Delete a flow alias |
| `create-flow-version` | Flows | Create a flow version |
| `get-flow-version` | Flows | Get flow version details |
| `list-flow-versions` | Flows | List flow versions |
| `delete-flow-version` | Flows | Delete a flow version |
| `tag-resource` | Tags | Add tags to a bedrock-agent resource |
| `untag-resource` | Tags | Remove tags from a bedrock-agent resource |
| `list-tags-for-resource` | Tags | List tags for a bedrock-agent resource |

### `aws bedrock-agent-runtime` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `create-invocation` | Agent Runtime | Create an agent invocation |
| `list-invocations` | Agent Runtime | List invocations |
| `get-invocation-step` | Agent Runtime | Get an invocation step |
| `list-invocation-steps` | Agent Runtime | List invocation steps |
| `put-invocation-step` | Agent Runtime | Create or update an invocation step |
| `create-session` | Agent Runtime | Create a session |
| `get-session` | Agent Runtime | Get session details |
| `list-sessions` | Agent Runtime | List sessions |
| `update-session` | Agent Runtime | Update a session |
| `delete-session` | Agent Runtime | Delete a session |
| `end-session` | Agent Runtime | End a session |
| `delete-agent-memory` | Agent Runtime | Delete agent memory |
| `get-agent-memory` | Agent Runtime | Retrieve agent memory |
| `retrieve` | RAG | Retrieve from a knowledge base |
| `retrieve-and-generate` | RAG | Retrieve and generate a response |
| `rerank` | RAG | Rerank search results |
| `generate-query` | RAG | Generate a query |
| `start-flow-execution` | Flows | Start a flow execution |
| `get-flow-execution` | Flows | Get flow execution details |
| `list-flow-executions` | Flows | List flow executions |
| `list-flow-execution-events` | Flows | List flow execution events |
| `stop-flow-execution` | Flows | Stop a flow execution |
| `get-execution-flow-snapshot` | Flows | Get execution flow snapshot |
| `tag-resource` | Tags | Add tags to a runtime resource |
| `untag-resource` | Tags | Remove tags from a runtime resource |
| `list-tags-for-resource` | Tags | List tags for a runtime resource |

### `aws bedrock-runtime` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `invoke-model` | Runtime | Invoke a model for single inference |
| `converse` | Runtime | Send messages in a multi-turn conversation |
| `apply-guardrail` | Runtime | Apply guardrail policies to content |
| `count-tokens` | Runtime | Count tokens in a prompt |
| `start-async-invoke` | Runtime | Start an asynchronous model invocation |
| `get-async-invoke` | Runtime | Get async invocation details |
| `list-async-invokes` | Runtime | List async invocations |

---

## Global Options

These options are available on ALL `aws bedrock`, `aws bedrock-agent`, `aws bedrock-agent-runtime`, and `aws bedrock-runtime` commands.

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

### Model ID Formats
| Format | Example |
|--------|---------|
| Base model ID | `anthropic.claude-3-sonnet-20240229-v1:0` |
| Base model ARN | `arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0` |
| Custom model ARN | `arn:aws:bedrock:us-east-1:123456789012:custom-model/my-model` |
| Provisioned throughput ARN | `arn:aws:bedrock:us-east-1:123456789012:provisioned-model/my-pt` |
| Inference profile ID | `us.anthropic.claude-3-sonnet-20240229-v1:0` |
| Imported model ARN | `arn:aws:bedrock:us-east-1:123456789012:imported-model/my-model` |

### Guardrail Content Filter Types
| Type | Description |
|------|-------------|
| `SEXUAL` | Sexual content |
| `VIOLENCE` | Violent content |
| `HATE` | Hate speech |
| `INSULTS` | Insulting content |
| `MISCONDUCT` | Misconduct guidance |
| `PROMPT_ATTACK` | Prompt injection attempts |

### Filter Strength Levels
`NONE` | `LOW` | `MEDIUM` | `HIGH`

### Knowledge Base Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Knowledge base is being created |
| `ACTIVE` | Knowledge base is ready for use |
| `DELETING` | Knowledge base is being deleted |
| `UPDATING` | Knowledge base is being updated |
| `FAILED` | Knowledge base creation/update failed |
| `DELETE_UNSUCCESSFUL` | Deletion failed |

### Agent Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Agent is being created |
| `PREPARING` | Agent is being prepared |
| `PREPARED` | Agent is ready for use |
| `NOT_PREPARED` | Agent needs to be prepared |
| `FAILED` | Agent creation/preparation failed |
| `UPDATING` | Agent is being updated |
| `DELETING` | Agent is being deleted |
| `VERSIONING` | Agent version is being created |

### Customization Types
| Type | Description |
|------|-------------|
| `FINE_TUNING` | Fine-tune a model on custom data |
| `CONTINUED_PRE_TRAINING` | Continue pre-training on additional data |
| `DISTILLATION` | Distill from a teacher model |
| `REINFORCEMENT_FINE_TUNING` | Fine-tune with reinforcement learning |

### Flow Node Types
`Input` | `Output` | `KnowledgeBase` | `Condition` | `Lex` | `Prompt` | `LambdaFunction` | `Storage` | `Agent` | `Retrieval` | `Iterator` | `Collector` | `InlineCode` | `Loop` | `LoopInput` | `LoopController`
