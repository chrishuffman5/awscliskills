# Amazon Q in Connect CLI Reference

Amazon Q in Connect (formerly Amazon Connect Wisdom) is an AI-powered assistant for contact center agents. It provides real-time recommendations, knowledge base search, quick responses, message templates, and AI agent capabilities powered by generative AI.

## Common Workflows

### Set Up an Assistant with Knowledge Base

```bash
# Create an assistant
aws qconnect create-assistant \
    --name "support-assistant" \
    --type AGENT

# Create a knowledge base
aws qconnect create-knowledge-base \
    --name "support-kb" \
    --knowledge-base-type CUSTOM

# Associate knowledge base with assistant
aws qconnect create-assistant-association \
    --assistant-id "assistant-uuid" \
    --association-type KNOWLEDGE_BASE \
    --association '{"knowledgeBaseId":"kb-uuid"}'

# Upload and create content
aws qconnect start-content-upload \
    --knowledge-base-id "kb-uuid" \
    --content-type "text/plain"

aws qconnect create-content \
    --knowledge-base-id "kb-uuid" \
    --name "troubleshooting-guide" \
    --upload-id "upload-id-from-above"
```

### Configure AI Agents and Prompts

```bash
# Create an AI prompt
aws qconnect create-ai-prompt \
    --assistant-id "assistant-uuid" \
    --name "answer-prompt" \
    --type ANSWER_GENERATION \
    --template-type TEXT \
    --model-id "anthropic.claude-3-sonnet-20240229-v1:0" \
    --api-format ANTHROPIC_CLAUDE_MESSAGES \
    --visibility-status PUBLISHED \
    --template-configuration '{"textFullAIPromptEditTemplateConfiguration":{"text":"Answer the question..."}}'

# Create an AI guardrail
aws qconnect create-ai-guardrail \
    --assistant-id "assistant-uuid" \
    --name "content-filter" \
    --blocked-input-messaging "Input blocked" \
    --blocked-outputs-messaging "Output blocked" \
    --visibility-status PUBLISHED \
    --content-policy-config '{"filtersConfig":[{"type":"HATE","inputStrength":"HIGH","outputStrength":"HIGH"}]}'

# Create an AI agent
aws qconnect create-ai-agent \
    --assistant-id "assistant-uuid" \
    --name "search-agent" \
    --type MANUAL_SEARCH \
    --visibility-status PUBLISHED \
    --configuration '{"manualSearchAIAgentConfiguration":{"answerGenerationAIPromptId":"prompt-uuid"}}'
```

### Session and Messaging

```bash
# Create a session
aws qconnect create-session \
    --assistant-id "assistant-uuid" \
    --name "session-001"

# Send a message
aws qconnect send-message \
    --assistant-id "assistant-uuid" \
    --session-id "session-uuid" \
    --type TEXT \
    --message '{"value":{"text":{"value":"How do I reset a password?"}}}'

# Get next message (AI response)
aws qconnect get-next-message \
    --assistant-id "assistant-uuid" \
    --session-id "session-uuid" \
    --next-message-token "token-from-send"
```

### Quick Responses and Message Templates

```bash
# Create a quick response
aws qconnect create-quick-response \
    --knowledge-base-id "kb-uuid" \
    --name "greeting" \
    --content '{"content":"Hello! How can I help you today?"}' \
    --language en_US

# Create a message template
aws qconnect create-message-template \
    --knowledge-base-id "kb-uuid" \
    --channel-subtype EMAIL \
    --name "welcome-email" \
    --content '{"email":{"subject":"Welcome","body":{"plainText":{"content":"Welcome to our service."}}}}'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Assistants | [`assistants.md`](assistants.md) | `create-assistant`, `get-assistant`, `list-assistants`, `delete-assistant`, `update-assistant-ai-agent`, `remove-assistant-ai-agent`, `create-assistant-association`, `get-assistant-association`, `list-assistant-associations`, `delete-assistant-association` |
| Knowledge Bases | [`knowledge-bases.md`](knowledge-bases.md) | `create-knowledge-base`, `get-knowledge-base`, `list-knowledge-bases`, `delete-knowledge-base`, `update-knowledge-base-template-uri`, `remove-knowledge-base-template-uri` |
| Content | [`content.md`](content.md) | `create-content`, `get-content`, `get-content-summary`, `list-contents`, `search-content`, `update-content`, `delete-content`, `start-content-upload`, `create-content-association`, `get-content-association`, `list-content-associations`, `delete-content-association` |
| Quick Responses | [`quick-responses.md`](quick-responses.md) | `create-quick-response`, `get-quick-response`, `list-quick-responses`, `search-quick-responses`, `update-quick-response`, `delete-quick-response` |
| AI Agents | [`ai-agents.md`](ai-agents.md) | `create-ai-agent`, `create-ai-agent-version`, `get-ai-agent`, `list-ai-agents`, `list-ai-agent-versions`, `update-ai-agent`, `delete-ai-agent`, `delete-ai-agent-version` |
| AI Guardrails | [`ai-guardrails.md`](ai-guardrails.md) | `create-ai-guardrail`, `create-ai-guardrail-version`, `get-ai-guardrail`, `list-ai-guardrails`, `list-ai-guardrail-versions`, `update-ai-guardrail`, `delete-ai-guardrail`, `delete-ai-guardrail-version` |
| AI Prompts | [`ai-prompts.md`](ai-prompts.md) | `create-ai-prompt`, `create-ai-prompt-version`, `get-ai-prompt`, `list-ai-prompts`, `list-ai-prompt-versions`, `update-ai-prompt`, `delete-ai-prompt`, `delete-ai-prompt-version` |
| Message Templates | [`message-templates.md`](message-templates.md) | `create-message-template`, `create-message-template-version`, `create-message-template-attachment`, `get-message-template`, `list-message-templates`, `list-message-template-versions`, `search-message-templates`, `render-message-template`, `update-message-template`, `update-message-template-metadata`, `activate-message-template`, `deactivate-message-template`, `delete-message-template`, `delete-message-template-attachment` |
| Sessions | [`sessions.md`](sessions.md) | `create-session`, `get-session`, `update-session`, `update-session-data`, `search-sessions`, `send-message`, `get-next-message`, `list-messages`, `retrieve` |
| Recommendations | [`recommendations.md`](recommendations.md) | `notify-recommendations-received`, `put-feedback`, `list-spans` |
| Import Jobs | [`import-jobs.md`](import-jobs.md) | `start-import-job`, `get-import-job`, `list-import-jobs`, `delete-import-job` |
| Tags | [`tags.md`](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
