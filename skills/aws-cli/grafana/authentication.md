# Authentication

### 2.1 `describe-workspace-authentication`

Displays information about the authentication methods used in one Amazon Managed Grafana workspace.

**Synopsis:**
```bash
aws grafana describe-workspace-authentication \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |

**Output Schema:**
```json
{
    "authentication": {
        "providers": ["AWS_SSO|SAML"],
        "samlConfigurationStatus": "CONFIGURED|NOT_CONFIGURED",
        "awsSso": {
            "ssoClientId": "string"
        },
        "saml": {
            "configuration": {
                "idpMetadata": {
                    "url": "string",
                    "xml": "string"
                },
                "assertionAttributes": {
                    "name": "string",
                    "login": "string",
                    "email": "string",
                    "groups": "string",
                    "role": "string",
                    "org": "string"
                },
                "roleValues": {
                    "editor": ["string"],
                    "admin": ["string"]
                },
                "allowedOrganizations": ["string"],
                "loginValidityDuration": "integer"
            },
            "status": "CONFIGURED|NOT_CONFIGURED"
        }
    }
}
```

---

### 2.2 `update-workspace-authentication`

Updates the authentication methods used in one Amazon Managed Grafana workspace.

**Synopsis:**
```bash
aws grafana update-workspace-authentication \
    --workspace-id <value> \
    --authentication-providers <value> \
    [--saml-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--authentication-providers` | **Yes** | list(string) | -- | Auth providers: `AWS_SSO`, `SAML` |
| `--saml-configuration` | No | structure | None | SAML configuration |

**SAML Configuration Structure:**
```json
{
    "idpMetadata": {
        "url": "string",
        "xml": "string"
    },
    "assertionAttributes": {
        "name": "string",
        "login": "string",
        "email": "string",
        "groups": "string",
        "role": "string",
        "org": "string"
    },
    "roleValues": {
        "editor": ["string"],
        "admin": ["string"]
    },
    "allowedOrganizations": ["string"],
    "loginValidityDuration": "integer"
}
```

**Output Schema:**
```json
{
    "authentication": {
        "providers": ["AWS_SSO|SAML"],
        "samlConfigurationStatus": "CONFIGURED|NOT_CONFIGURED",
        "awsSso": {
            "ssoClientId": "string"
        },
        "saml": {
            "configuration": {
                "idpMetadata": {},
                "assertionAttributes": {},
                "roleValues": {},
                "allowedOrganizations": [],
                "loginValidityDuration": "integer"
            },
            "status": "CONFIGURED|NOT_CONFIGURED"
        }
    }
}
```
