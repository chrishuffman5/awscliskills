# Workforce

## 1. `create-workforce`

Creates a workforce for labeling jobs (Cognito, OIDC, or private).

**Synopsis:**
```bash
aws sagemaker create-workforce \
    --workforce-name <value> \
    [--cognito-config <value>] \
    [--oidc-config <value>] \
    [--source-ip-config <value>] \
    [--workforce-vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workforce-name` | **Yes** | string | -- | Workforce name |
| `--cognito-config` | No | structure | -- | `UserPool`, `ClientId` |
| `--oidc-config` | No | structure | -- | OIDC provider config (`Issuer`, `ClientId`, `ClientSecret`, `AuthorizationEndpoint`, `TokenEndpoint`, `UserInfoEndpoint`, `LogoutEndpoint`, `JwksUri`) |
| `--source-ip-config` | No | structure | -- | `Cidrs` for IP allowlist |
| `--workforce-vpc-config` | No | structure | -- | VPC config |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "Workforce": {
        "WorkforceName": "string",
        "WorkforceArn": "string",
        "LastUpdatedDate": "timestamp",
        "SourceIpConfig": {"Cidrs": ["string"]},
        "SubDomain": "string",
        "CognitoConfig": {...},
        "OidcConfig": {...},
        "CreateDate": "timestamp",
        "WorkforceVpcConfig": {...},
        "Status": "Initializing|Active|Updating|Deleting|Failed",
        "FailureReason": "string"
    }
}
```

---

## 2. `describe-workforce` / `list-workforces` / `update-workforce` / `delete-workforce`

```bash
aws sagemaker describe-workforce --workforce-name <value>
aws sagemaker list-workforces [--sort-by <value>] [--sort-order <value>] [--name-contains <value>]
aws sagemaker update-workforce --workforce-name <value> [--source-ip-config <value>] [--oidc-config <value>] [--workforce-vpc-config <value>]
aws sagemaker delete-workforce --workforce-name <value>
```

---

## 3. `create-workteam`

Creates a workteam for labeling jobs.

```bash
aws sagemaker create-workteam \
    --workteam-name <value> \
    --member-definitions <value> \
    --description <value> \
    [--workforce-name <value>] \
    [--notification-configuration <value>] \
    [--worker-access-configuration <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workteam-name` | **Yes** | string | -- | Workteam name |
| `--member-definitions` | **Yes** | list | -- | Team members (`CognitoMemberDefinition` or `OidcMemberDefinition`) |
| `--description` | **Yes** | string | -- | Team description |
| `--workforce-name` | No | string | -- | Workforce name |
| `--notification-configuration` | No | structure | -- | SNS topic ARN for notifications |

**Output Schema:**
```json
{
    "WorkteamArn": "string"
}
```

---

## 4. `describe-workteam` / `list-workteams` / `update-workteam` / `delete-workteam`

```bash
aws sagemaker describe-workteam --workteam-name <value>
aws sagemaker list-workteams [--sort-by <value>] [--sort-order <value>] [--name-contains <value>]
aws sagemaker update-workteam --workteam-name <value> [--member-definitions <value>] [--description <value>] [--notification-configuration <value>]
aws sagemaker delete-workteam --workteam-name <value>
```

---

## 5. `describe-subscribed-workteam` / `list-subscribed-workteams`

Access information about AWS Marketplace subscribed workteams.

```bash
aws sagemaker describe-subscribed-workteam --workteam-arn <value>
aws sagemaker list-subscribed-workteams [--name-contains <value>]
```
