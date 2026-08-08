# Foundation Models

> **Note:** Six model-access commands — `list-foundation-model-agreement-offers`, `create-foundation-model-agreement`, `delete-foundation-model-agreement`, `get-foundation-model-availability`, `put-use-case-for-model-access`, and `get-use-case-for-model-access` — were made public in **AWS CLI v2.27.42** (released 2025-06-24); they were previously console-only. Requires AWS CLI ≥ 2.27.42; older versions return an unknown-command error.

## Model Access Workflow

How to get a foundation model ready to invoke:

- **Serverless models (default):** As of October 2025, serverless foundation models are enabled by default in all commercial regions — no manual model-access toggling is required.
- **Anthropic models:** Still require a one-time first-time-use (FTU) form. Submit it with `put-use-case-for-model-access`; retrieve the previously submitted form with `get-use-case-for-model-access`. The submission is account-level (a submission at the AWS Organizations management account is inherited by member accounts) and is not per-model. It does not apply to Anthropic models accessed via the bedrock-mantle endpoint.
- **Marketplace-gated models:** Call `list-foundation-model-agreement-offers` to obtain an `offerToken`, then `create-foundation-model-agreement` with that token.
- **Readiness check:** `get-foundation-model-availability` returns `agreementAvailability.status` (`AVAILABLE` | `PENDING` | `IN_PROGRESS` | `NOT_AVAILABLE`), `authorizationStatus` (`AUTHORIZED` | `NOT_AUTHORIZED`), and `entitlementAvailability` (`AVAILABLE` | `NOT_AVAILABLE`).
- **Prerequisites:** The caller needs `aws-marketplace:Subscribe`, `aws-marketplace:Unsubscribe`, and `aws-marketplace:ViewSubscriptions`, plus a valid payment method on the account. The first invocation auto-initiates the subscription; allow up to ~15 minutes for propagation, during which `AccessDeniedException` can appear transiently.

### Example: model access with an SSO profile

When you authenticate through IAM Identity Center (AWS SSO), run the model-access commands against the SSO-enabled profile. The permission set behind that profile must grant the Bedrock and Marketplace actions below — model access applies to the account the profile assumes a role in.

```bash
# 1. Log in (caches an SSO access token; see ../sso/login-logout.md)
aws sso login --sso-session my-sso

# 2. Confirm which account/role the profile resolves to
aws sts get-caller-identity --profile bedrock-admin

# 3. Submit the Anthropic FTU form for that account
aws bedrock put-use-case-for-model-access \
    --form-data fileb://anthropic-use-case-form.json \
    --profile bedrock-admin \
    --region us-east-1

# 4. Confirm readiness for a specific model
aws bedrock get-foundation-model-availability \
    --model-id anthropic.claude-3-5-sonnet-20241022-v2:0 \
    --profile bedrock-admin \
    --region us-east-1
```

The `[profile bedrock-admin]` block references an `[sso-session my-sso]` (see [`../sso/configure-sso.md`](../sso/configure-sso.md)). The permission set must allow `bedrock:PutUseCaseForModelAccess`, `bedrock:GetUseCaseForModelAccess`, `bedrock:GetFoundationModelAvailability`, `bedrock:ListFoundationModelAgreementOffers`, `bedrock:CreateFoundationModelAgreement`, plus the `aws-marketplace:*` actions listed above. A short-lived SSO token can expire mid-workflow — if a call returns an expired-token error, re-run `aws sso login` (see [`../sso/login-logout.md`](../sso/login-logout.md)).

---

### `list-foundation-models`

Lists Amazon Bedrock foundation models that you can use. You can filter the results by provider, output modality, customization type, and inference type.

**Synopsis:**
```bash
aws bedrock list-foundation-models \
    [--by-provider <value>] \
    [--by-customization-type <value>] \
    [--by-output-modality <value>] \
    [--by-inference-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--by-provider` | No | string | None | Filter by model provider (e.g., `Anthropic`, `Amazon`, `Meta`). Pattern: `[A-Za-z0-9- ]{1,63}` |
| `--by-customization-type` | No | string | None | Filter by customization type: `FINE_TUNING`, `CONTINUED_PRE_TRAINING`, `DISTILLATION` |
| `--by-output-modality` | No | string | None | Filter by output modality: `TEXT`, `IMAGE`, `EMBEDDING` |
| `--by-inference-type` | No | string | None | Filter by inference type: `ON_DEMAND`, `PROVISIONED` |

**Output Schema:**
```json
{
    "modelSummaries": [
        {
            "modelArn": "string",
            "modelId": "string",
            "modelName": "string",
            "providerName": "string",
            "inputModalities": ["TEXT|IMAGE|EMBEDDING"],
            "outputModalities": ["TEXT|IMAGE|EMBEDDING"],
            "responseStreamingSupported": true|false,
            "customizationsSupported": ["FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION"],
            "inferenceTypesSupported": ["ON_DEMAND|PROVISIONED"],
            "modelLifecycle": {
                "status": "ACTIVE|LEGACY"
            }
        }
    ]
}
```

---

### `get-foundation-model`

Gets details about a specified Amazon Bedrock foundation model.

**Synopsis:**
```bash
aws bedrock get-foundation-model \
    --model-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-identifier` | **Yes** | string | -- | The model ID or ARN. Min: 1, Max: 2048 |

**Output Schema:**
```json
{
    "modelDetails": {
        "modelArn": "string",
        "modelId": "string",
        "modelName": "string",
        "providerName": "string",
        "inputModalities": ["TEXT|IMAGE|EMBEDDING"],
        "outputModalities": ["TEXT|IMAGE|EMBEDDING"],
        "responseStreamingSupported": true|false,
        "customizationsSupported": ["FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION"],
        "inferenceTypesSupported": ["ON_DEMAND|PROVISIONED"],
        "modelLifecycle": {
            "status": "ACTIVE|LEGACY"
        }
    }
}
```

---

### `list-foundation-model-agreement-offers`

Lists agreement offers for a specified foundation model.

> **Note:** Requires AWS CLI ≥ 2.27.42 (released 2025-06-24); older versions return an unknown-command error.

**Synopsis:**
```bash
aws bedrock list-foundation-model-agreement-offers \
    --model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to list agreement offers for |

**Output Schema:**
```json
{
    "modelId": "string",
    "offers": [
        {
            "offerToken": "string"
        }
    ]
}
```

---

### `create-foundation-model-agreement`

Creates an agreement for a specified foundation model.

> **Note:** Requires AWS CLI ≥ 2.27.42 (released 2025-06-24); older versions return an unknown-command error.

**Synopsis:**
```bash
aws bedrock create-foundation-model-agreement \
    --model-id <value> \
    --offer-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to create the agreement for |
| `--offer-token` | **Yes** | string | -- | The offer token for the agreement |

**Output Schema:**
```json
{
    "modelId": "string"
}
```

---

### `delete-foundation-model-agreement`

Deletes an agreement for a specified foundation model.

> **Note:** Requires AWS CLI ≥ 2.27.42 (released 2025-06-24); older versions return an unknown-command error.

**Synopsis:**
```bash
aws bedrock delete-foundation-model-agreement \
    --model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to delete the agreement for |

**Output:** None (HTTP 200 on success)

---

### `get-foundation-model-availability`

Gets the availability of a foundation model.

> **Note:** Requires AWS CLI ≥ 2.27.42 (released 2025-06-24); older versions return an unknown-command error.

**Synopsis:**
```bash
aws bedrock get-foundation-model-availability \
    --model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to check availability for |

**Output Schema:**
```json
{
    "modelId": "string",
    "agreementAvailability": {
        "status": "AVAILABLE|PENDING|IN_PROGRESS|NOT_AVAILABLE"
    },
    "authorizationStatus": "AUTHORIZED|NOT_AUTHORIZED",
    "entitlementAvailability": "AVAILABLE|NOT_AVAILABLE"
}
```

---

### `put-use-case-for-model-access`

Submits the one-time first-time-use (FTU) form required for access to Anthropic models. The submission is account-level (a submission at the AWS Organizations management account is inherited by member accounts) and is not per-model.

> **Note:** Requires AWS CLI ≥ 2.27.42 (released 2025-06-24); older versions return an unknown-command error.

**Synopsis:**
```bash
aws bedrock put-use-case-for-model-access \
    --form-data <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--form-data` | **Yes** | blob | -- | The FTU form payload. Min: 10, Max: 16384 bytes. The default CLI binary format is base64; use `fileb://` to pass raw bytes from a file (`fileb://` is always treated as binary regardless of `--cli-binary-format`). |

> **Note:** The exact JSON schema of the form blob is not cleanly published. Use `--generate-cli-skeleton` to reveal the input shape; in practice the console playground is the simplest first-time path for producing a valid form.

**Form fields:** The `formData` blob is a JSON document. The field names below are derived from the Bedrock console form and community automation, not an officially published API schema — verify against `--generate-cli-skeleton` for your CLI version.

| Field | Required | Description |
|-------|----------|-------------|
| `companyName` | Yes | Legal/organization name |
| `companyWebsite` | Yes | Company URL — validation requires the `www.` prefix |
| `intendedUsers` | Yes | Enumerated string: `"0"` = internal employees only, `"1"` = external end users |
| `industryOption` | Yes | Industry category (e.g. `Technology`, `Financial Services`, `Healthcare`, `Education`, `Retail`, `Government`, `Other`) |
| `otherIndustryOption` | Conditional | Free text — set only when `industryOption` is `Other`, otherwise `""` |
| `useCases` | Yes | Free-text description of intended model usage |

**Example form (fictional company):**
```json
{
  "companyName": "Meridian Insights, Inc.",
  "companyWebsite": "https://www.meridian-insights.com/",
  "intendedUsers": "0",
  "industryOption": "Technology",
  "otherIndustryOption": "",
  "useCases": "Meridian Insights operates a B2B SaaS analytics platform for supply-chain teams. We intend to use Anthropic Claude models on Amazon Bedrock to (1) summarize internal logistics and inventory reports, (2) power an internal natural-language assistant that lets our analysts query operational dashboards, and (3) draft and classify internal support tickets. All outputs are reviewed by employees before any business action is taken; the models are not used for fully automated decisions, and raw model output is not exposed directly to external end users. We will comply with Anthropic's Acceptable Use Policy and the AWS service terms."
}
```

Save the JSON to a file and submit it as raw bytes with `fileb://`. The whole document is the blob, so keep it within the 10–16384 byte limit (the example above is ~840 bytes).
```bash
aws bedrock put-use-case-for-model-access \
    --form-data fileb://anthropic-use-case-form.json \
    --region us-east-1
```

**Output:** None (HTTP 201 on success)

---

### `get-use-case-for-model-access`

Retrieves the first-time-use (FTU) form previously submitted for Anthropic model access. The scope is account-level (a submission at the AWS Organizations management account is inherited by member accounts) and is not per-model. Does not apply to Anthropic models accessed via the bedrock-mantle endpoint.

> **Note:** Requires AWS CLI ≥ 2.27.42 (released 2025-06-24); older versions return an unknown-command error.

**Synopsis:**
```bash
aws bedrock get-use-case-for-model-access \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

This command has no required parameters (only the standard global options).

**Output Schema:**
```json
{
    "formData": "blob"
}
```

`formData` is a base64-encoded blob (length 10–16384 bytes) holding the FTU form previously submitted.

> **Note:** A `ResourceNotFoundException` means no form has been submitted yet — use it as the "not submitted" signal. Other errors: `ValidationException`, `InternalServerException`, `ThrottlingException`.
