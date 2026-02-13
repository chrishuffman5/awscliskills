# Directory Configs

### 8.1 `create-directory-config`

Creates a directory configuration for Active Directory domain join.

**Synopsis:**
```bash
aws appstream create-directory-config \
    --directory-name <value> \
    --organizational-unit-distinguished-names <value> \
    [--service-account-credentials <value>] \
    [--certificate-based-auth-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-name` | **Yes** | string | -- | Fully qualified name of the directory (e.g., `corp.example.com`) |
| `--organizational-unit-distinguished-names` | **Yes** | list(string) | -- | Distinguished names of OUs for computer accounts |
| `--service-account-credentials` | No | structure | -- | Service account credentials. Shorthand: `AccountName=string,AccountPassword=string` |
| `--certificate-based-auth-properties` | No | structure | -- | Certificate-based auth. Shorthand: `Status=DISABLED\|ENABLED\|ENABLED_NO_DIRECTORY_LOGIN_FALLBACK,CertificateAuthorityArn=string` |

**Output Schema:**
```json
{
    "DirectoryConfig": {
        "DirectoryName": "string",
        "OrganizationalUnitDistinguishedNames": ["string"],
        "ServiceAccountCredentials": {
            "AccountName": "string",
            "AccountPassword": "string"
        },
        "CreatedTime": "timestamp",
        "CertificateBasedAuthProperties": {
            "Status": "DISABLED|ENABLED|ENABLED_NO_DIRECTORY_LOGIN_FALLBACK",
            "CertificateAuthorityArn": "string"
        }
    }
}
```

---

### 8.2 `delete-directory-config`

Deletes the specified directory configuration. Cannot delete if in use by fleets or image builders.

**Synopsis:**
```bash
aws appstream delete-directory-config \
    --directory-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-name` | **Yes** | string | -- | Fully qualified name of the directory |

**Output Schema:**
```json
{}
```

---

### 8.3 `describe-directory-configs`

Describes directory configurations.

**Synopsis:**
```bash
aws appstream describe-directory-configs \
    [--directory-names <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-names` | No | list(string) | -- | Directory names to describe |
| `--max-results` | No | integer | -- | Maximum number of results |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "DirectoryConfigs": [
        {
            "DirectoryName": "string",
            "OrganizationalUnitDistinguishedNames": ["string"],
            "ServiceAccountCredentials": {
                "AccountName": "string",
                "AccountPassword": "string"
            },
            "CreatedTime": "timestamp",
            "CertificateBasedAuthProperties": {
                "Status": "DISABLED|ENABLED|ENABLED_NO_DIRECTORY_LOGIN_FALLBACK",
                "CertificateAuthorityArn": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `update-directory-config`

Updates the specified directory configuration.

**Synopsis:**
```bash
aws appstream update-directory-config \
    --directory-name <value> \
    [--organizational-unit-distinguished-names <value>] \
    [--service-account-credentials <value>] \
    [--certificate-based-auth-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-name` | **Yes** | string | -- | Fully qualified name of the directory |
| `--organizational-unit-distinguished-names` | No | list(string) | -- | Distinguished names of OUs |
| `--service-account-credentials` | No | structure | -- | Service account credentials |
| `--certificate-based-auth-properties` | No | structure | -- | Certificate-based auth properties |

**Output Schema:**
```json
{
    "DirectoryConfig": {
        "DirectoryName": "string",
        "OrganizationalUnitDistinguishedNames": ["string"],
        "ServiceAccountCredentials": {
            "AccountName": "string",
            "AccountPassword": "string"
        },
        "CreatedTime": "timestamp",
        "CertificateBasedAuthProperties": {
            "Status": "DISABLED|ENABLED|ENABLED_NO_DIRECTORY_LOGIN_FALLBACK",
            "CertificateAuthorityArn": "string"
        }
    }
}
```
