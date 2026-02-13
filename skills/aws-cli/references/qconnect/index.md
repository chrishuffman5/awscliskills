# Q Connect Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `activate-message-template` | Activates a message template version |
| `create-ai-agent` | Creates an AI agent for an assistant |
| `create-ai-agent-version` | Creates an immutable AI agent version |
| `create-ai-guardrail` | Creates content filtering guardrails |
| `create-ai-guardrail-version` | Creates an immutable guardrail version |
| `create-ai-prompt` | Creates a prompt template for AI agents |
| `create-ai-prompt-version` | Creates an immutable prompt version |
| `create-assistant` | Creates an Amazon Q in Connect assistant |
| `create-assistant-association` | Associates a knowledge base with assistant |
| `create-content` | Creates content in a knowledge base |
| `create-content-association` | Creates a content association |
| `create-message-template` | Creates a message template |
| `create-message-template-attachment` | Attaches a file to a message template |
| `create-message-template-version` | Creates an immutable template version |
| `create-quick-response` | Creates a quick response |
| `create-session` | Creates a session for recommendations |
| `deactivate-message-template` | Deactivates a message template version |
| `delete-ai-agent` | Deletes an AI agent |
| `delete-ai-agent-version` | Deletes an AI agent version |
| `delete-ai-guardrail` | Deletes an AI guardrail |
| `delete-ai-guardrail-version` | Deletes an AI guardrail version |
| `delete-ai-prompt` | Deletes an AI prompt |
| `delete-ai-prompt-version` | Deletes an AI prompt version |
| `delete-assistant` | Deletes an assistant |
| `delete-assistant-association` | Deletes an assistant association |
| `delete-content` | Deletes content from a knowledge base |
| `delete-content-association` | Deletes a content association |
| `delete-import-job` | Deletes an import job |
| `delete-knowledge-base` | Deletes a knowledge base |
| `delete-message-template` | Deletes a message template |
| `delete-message-template-attachment` | Deletes a message template attachment |
| `delete-quick-response` | Deletes a quick response |
| `get-ai-agent` | Gets an AI agent |
| `get-ai-guardrail` | Gets an AI guardrail |
| `get-ai-prompt` | Gets an AI prompt |
| `get-assistant` | Gets an assistant |
| `get-assistant-association` | Gets an assistant association |
| `get-content` | Gets content from a knowledge base |
| `get-content-association` | Gets a content association |
| `get-content-summary` | Gets a content summary |
| `get-import-job` | Gets an import job |
| `get-knowledge-base` | Gets a knowledge base |
| `get-message-template` | Gets a message template |
| `get-next-message` | Gets next AI response message |
| `get-quick-response` | Gets a quick response |
| `get-session` | Gets session details |
| `list-ai-agent-versions` | Lists AI agent versions |
| `list-ai-agents` | Lists AI agents |
| `list-ai-guardrail-versions` | Lists AI guardrail versions |
| `list-ai-guardrails` | Lists AI guardrails |
| `list-ai-prompt-versions` | Lists AI prompt versions |
| `list-ai-prompts` | Lists AI prompts |
| `list-assistant-associations` | Lists assistant associations |
| `list-assistants` | Lists assistants |
| `list-content-associations` | Lists content associations |
| `list-contents` | Lists content in a knowledge base |
| `list-import-jobs` | Lists import jobs |
| `list-knowledge-bases` | Lists knowledge bases |
| `list-message-template-versions` | Lists message template versions |
| `list-message-templates` | Lists message templates |
| `list-messages` | Lists messages in a session |
| `list-quick-responses` | Lists quick responses |
| `list-spans` | Lists monitoring spans |
| `list-tags-for-resource` | Lists tags for a resource |
| `notify-recommendations-received` | Marks recommendations as received |
| `put-feedback` | Provides feedback on recommendations |
| `remove-assistant-ai-agent` | Removes AI agent from assistant |
| `remove-knowledge-base-template-uri` | Removes template URI from knowledge base |
| `render-message-template` | Renders a message template with values |
| `retrieve` | Retrieves content from knowledge base |
| `search-content` | Searches content in a knowledge base |
| `search-message-templates` | Searches message templates |
| `search-quick-responses` | Searches quick responses |
| `search-sessions` | Searches sessions |
| `send-message` | Sends a message to an AI agent |
| `start-content-upload` | Gets a pre-signed URL for content upload |
| `start-import-job` | Starts a bulk import job |
| `tag-resource` | Adds tags to a resource |
| `untag-resource` | Removes tags from a resource |
| `update-ai-agent` | Updates an AI agent |
| `update-ai-guardrail` | Updates an AI guardrail |
| `update-ai-prompt` | Updates an AI prompt |
| `update-content` | Updates content in a knowledge base |
| `update-knowledge-base-template-uri` | Updates knowledge base template URI |
| `update-message-template` | Updates a message template |
| `update-message-template-metadata` | Updates message template metadata |
| `update-quick-response` | Updates a quick response |
| `update-session` | Updates a session |
| `update-session-data` | Updates session data |

## AI Agent Types

| Type | Description |
|------|-------------|
| `MANUAL_SEARCH` | Agent-initiated search |
| `ANSWER_RECOMMENDATION` | Real-time answer recommendations |
| `SELF_SERVICE` | Customer self-service |
| `EMAIL_RESPONSE` | Email response generation |
| `EMAIL_OVERVIEW` | Email overview generation |
| `EMAIL_GENERATIVE_ANSWER` | Email generative answers |
| `ORCHESTRATION` | Orchestration agent |
| `NOTE_TAKING` | Note taking agent |
| `CASE_SUMMARIZATION` | Case summarization agent |

## AI Prompt Types

| Type | Description |
|------|-------------|
| `ANSWER_GENERATION` | Generate answers |
| `INTENT_LABELING_GENERATION` | Label intents |
| `QUERY_REFORMULATION` | Reformulate queries |
| `SELF_SERVICE_PRE_PROCESSING` | Pre-process self-service |
| `SELF_SERVICE_ANSWER_GENERATION` | Generate self-service answers |
| `EMAIL_RESPONSE` | Generate email responses |
| `ORCHESTRATION` | Orchestrate tool use |
| `NOTE_TAKING` | Generate notes |
| `CASE_SUMMARIZATION` | Summarize cases |

## Knowledge Base Types

| Type | Description |
|------|-------------|
| `CUSTOM` | Upload your own content |
| `EXTERNAL` | Third-party integrations (Salesforce, ServiceNow) |
| `QUICK_RESPONSES` | Quick response knowledge base |
| `MESSAGE_TEMPLATES` | Message template knowledge base |
| `MANAGED` | Managed sources (web crawling) |

## Visibility Statuses

| Status | Description |
|--------|-------------|
| `SAVED` | Draft state, not yet active |
| `PUBLISHED` | Active and ready for use |

## Channel Subtypes (Message Templates)

`EMAIL`, `SMS`, `WHATSAPP`, `PUSH`

## Global Options

All `aws qconnect` commands support these options:

| Option | Description |
|--------|-------------|
| `--region` | AWS region |
| `--profile` | Named profile |
| `--output` | Output format: `json`, `text`, `table`, `yaml` |
| `--query` | JMESPath query |
| `--no-cli-pager` | Disable pager |
| `--cli-input-json` | Read input from JSON |
| `--generate-cli-skeleton` | Generate input skeleton |
