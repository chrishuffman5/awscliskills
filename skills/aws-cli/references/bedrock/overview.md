# AWS CLI v2 — Amazon Bedrock

## Overview

Complete reference for `aws bedrock`, `aws bedrock-agent`, `aws bedrock-agent-runtime`, and `aws bedrock-runtime` subcommands in AWS CLI v2. Covers foundation model management, model customization (fine-tuning, continued pre-training, distillation), provisioned throughput, guardrails, inference profiles, evaluation jobs, batch inference, marketplace models, automated reasoning, agents, knowledge bases, prompts, flows, RAG retrieval and generation, and real-time model invocation.

## Quick Reference — Common Workflows

### List available foundation models
```bash
aws bedrock list-foundation-models \
  --by-output-modality TEXT \
  --query 'modelSummaries[].{Id:modelId,Name:modelName,Provider:providerName}' \
  --output table
```

### Invoke a model (single request)
```bash
aws bedrock-runtime invoke-model \
  --model-id anthropic.claude-3-sonnet-20240229-v1:0 \
  --content-type application/json \
  --body '{"anthropic_version":"bedrock-2023-05-31","max_tokens":1024,"messages":[{"role":"user","content":"Hello"}]}' \
  output.json
```

### Use the Converse API (multi-turn)
```bash
aws bedrock-runtime converse \
  --model-id anthropic.claude-3-sonnet-20240229-v1:0 \
  --messages '[{"role":"user","content":[{"text":"What is Amazon Bedrock?"}]}]' \
  --inference-config '{"maxTokens":512,"temperature":0.7}'
```

### Create a guardrail
```bash
aws bedrock create-guardrail \
  --name my-guardrail \
  --blocked-input-messaging "Input blocked by guardrail." \
  --blocked-outputs-messaging "Output blocked by guardrail." \
  --content-policy-config '{"filtersConfig":[{"type":"SEXUAL","inputStrength":"HIGH","outputStrength":"HIGH"},{"type":"VIOLENCE","inputStrength":"HIGH","outputStrength":"HIGH"}]}'
```

### Create an agent
```bash
aws bedrock-agent create-agent \
  --agent-name my-agent \
  --agent-resource-role-arn arn:aws:iam::123456789012:role/BedrockAgentRole \
  --foundation-model anthropic.claude-3-sonnet-20240229-v1:0 \
  --instruction "You are a helpful assistant that answers questions about our products."
```

### Create a knowledge base
```bash
aws bedrock-agent create-knowledge-base \
  --name my-kb \
  --role-arn arn:aws:iam::123456789012:role/BedrockKBRole \
  --knowledge-base-configuration '{"type":"VECTOR","vectorKnowledgeBaseConfiguration":{"embeddingModelArn":"arn:aws:bedrock:us-east-1::foundation-model/amazon.titan-embed-text-v1"}}' \
  --storage-configuration '{"type":"OPENSEARCH_SERVERLESS","opensearchServerlessConfiguration":{"collectionArn":"arn:aws:aoss:us-east-1:123456789012:collection/my-collection","vectorIndexName":"my-index","fieldMapping":{"vectorField":"embedding","textField":"text","metadataField":"metadata"}}}'
```

### Retrieve and generate from a knowledge base
```bash
aws bedrock-agent-runtime retrieve-and-generate \
  --input '{"text":"What are the return policies?"}' \
  --retrieve-and-generate-configuration '{"type":"KNOWLEDGE_BASE","knowledgeBaseConfiguration":{"knowledgeBaseId":"KB123456","modelArn":"arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0"}}'
```

### Start a model customization job (fine-tuning)
```bash
aws bedrock create-model-customization-job \
  --job-name my-finetune-job \
  --custom-model-name my-custom-model \
  --role-arn arn:aws:iam::123456789012:role/BedrockCustomizationRole \
  --base-model-identifier anthropic.claude-3-haiku-20240307-v1:0 \
  --training-data-config '{"s3Uri":"s3://my-bucket/training-data.jsonl"}' \
  --output-data-config '{"s3Uri":"s3://my-bucket/output/"}'
```

### Create a provisioned throughput
```bash
aws bedrock create-provisioned-model-throughput \
  --provisioned-model-name my-pt \
  --model-id anthropic.claude-3-sonnet-20240229-v1:0 \
  --model-units 1
```

### Create and run a flow
```bash
aws bedrock-agent create-flow \
  --name my-flow \
  --execution-role-arn arn:aws:iam::123456789012:role/BedrockFlowRole \
  --definition file://flow-definition.json

aws bedrock-agent prepare-flow --flow-identifier FLOW_ID

aws bedrock-agent-runtime start-flow-execution \
  --flow-identifier FLOW_ID \
  --flow-alias-identifier ALIAS_ID \
  --inputs '[{"nodeName":"InputNode","nodeOutputName":"document","content":{"document":{"text":"Hello"}}}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Foundation Models | [`foundation-models.md`](foundation-models.md) | list-foundation-models, get-foundation-model, list-foundation-model-agreement-offers, create-foundation-model-agreement, delete-foundation-model-agreement, get-foundation-model-availability |
| Custom Models | [`custom-models.md`](custom-models.md) | create-model-customization-job, get-model-customization-job, list-model-customization-jobs, stop-model-customization-job, create-custom-model, get-custom-model, list-custom-models, delete-custom-model, create-custom-model-deployment, get-custom-model-deployment, list-custom-model-deployments, delete-custom-model-deployment |
| Model Import & Copy | [`model-import-copy.md`](model-import-copy.md) | create-model-import-job, get-model-import-job, list-model-import-jobs, create-model-copy-job, get-model-copy-job, list-model-copy-jobs, get-imported-model, list-imported-models, delete-imported-model |
| Provisioned Throughput | [`provisioned-throughput.md`](provisioned-throughput.md) | create-provisioned-model-throughput, get-provisioned-model-throughput, list-provisioned-model-throughputs, update-provisioned-model-throughput, delete-provisioned-model-throughput |
| Guardrails | [`guardrails.md`](guardrails.md) | create-guardrail, get-guardrail, list-guardrails, update-guardrail, delete-guardrail, create-guardrail-version, get-guardrail-policy |
| Inference Profiles | [`inference-profiles.md`](inference-profiles.md) | create-inference-profile, get-inference-profile, list-inference-profiles, delete-inference-profile, create-prompt-router, get-prompt-router, list-prompt-routers, delete-prompt-router |
| Evaluation Jobs | [`evaluation-jobs.md`](evaluation-jobs.md) | create-evaluation-job, get-evaluation-job, list-evaluation-jobs, stop-evaluation-job, batch-delete-evaluation-job |
| Invocation Jobs | [`invocation-jobs.md`](invocation-jobs.md) | create-model-invocation-job, get-model-invocation-job, list-model-invocation-jobs, stop-model-invocation-job |
| Marketplace | [`marketplace.md`](marketplace.md) | create-marketplace-model-endpoint, get-marketplace-model-endpoint, list-marketplace-model-endpoints, update-marketplace-model-endpoint, delete-marketplace-model-endpoint, register-marketplace-model-endpoint, deregister-marketplace-model-endpoint |
| Automated Reasoning | [`automated-reasoning.md`](automated-reasoning.md) | create-automated-reasoning-policy, get-automated-reasoning-policy, list-automated-reasoning-policies, delete-automated-reasoning-policy, create-automated-reasoning-policy-version, create-automated-reasoning-policy-test-case, start-automated-reasoning-policy-build-workflow, cancel-automated-reasoning-policy-build-workflow, get-automated-reasoning-policy-build-workflow-status |
| Agents | [`agents.md`](agents.md) | create-agent, get-agent, list-agents, update-agent, delete-agent, prepare-agent, create-agent-alias, get-agent-alias, list-agent-aliases, update-agent-alias, delete-agent-alias, get-agent-version, list-agent-versions, delete-agent-version |
| Agent Action Groups | [`agent-action-groups.md`](agent-action-groups.md) | create-agent-action-group, get-agent-action-group, list-agent-action-groups, update-agent-action-group, delete-agent-action-group |
| Agent Knowledge Bases | [`agent-knowledge-bases.md`](agent-knowledge-bases.md) | associate-agent-knowledge-base, get-agent-knowledge-base, list-agent-knowledge-bases, update-agent-knowledge-base, disassociate-agent-knowledge-base, associate-agent-collaborator, get-agent-collaborator, list-agent-collaborators, update-agent-collaborator, disassociate-agent-collaborator |
| Knowledge Bases | [`knowledge-bases.md`](knowledge-bases.md) | create-knowledge-base, get-knowledge-base, list-knowledge-bases, update-knowledge-base, delete-knowledge-base, create-data-source, get-data-source, list-data-sources, update-data-source, delete-data-source, start-ingestion-job, get-ingestion-job, list-ingestion-jobs, stop-ingestion-job, ingest-knowledge-base-documents, get-knowledge-base-documents, list-knowledge-base-documents, delete-knowledge-base-documents |
| Prompts | [`prompts.md`](prompts.md) | create-prompt, get-prompt, list-prompts, update-prompt, delete-prompt, create-prompt-version |
| Flows | [`flows.md`](flows.md) | create-flow, get-flow, list-flows, update-flow, delete-flow, prepare-flow, validate-flow-definition, create-flow-alias, get-flow-alias, list-flow-aliases, update-flow-alias, delete-flow-alias, create-flow-version, get-flow-version, list-flow-versions, delete-flow-version |
| Agent Runtime | [`agent-runtime.md`](agent-runtime.md) | create-invocation, list-invocations, get-invocation-step, list-invocation-steps, put-invocation-step, create-session, get-session, list-sessions, update-session, delete-session, end-session, delete-agent-memory, get-agent-memory |
| Agent Runtime RAG | [`agent-runtime-rag.md`](agent-runtime-rag.md) | retrieve, retrieve-and-generate, rerank, generate-query |
| Agent Runtime Flows | [`agent-runtime-flows.md`](agent-runtime-flows.md) | start-flow-execution, get-flow-execution, list-flow-executions, list-flow-execution-events, stop-flow-execution, get-execution-flow-snapshot |
| Runtime | [`runtime.md`](runtime.md) | invoke-model, converse, apply-guardrail, count-tokens, start-async-invoke, get-async-invoke, list-async-invokes |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource (bedrock), tag-resource, untag-resource, list-tags-for-resource (bedrock-agent), tag-resource, untag-resource, list-tags-for-resource (bedrock-agent-runtime) |
