# Random Password

### 7.1 `get-random-password`

Generates a random password. Does not create or store a secret.

**Synopsis:**
```bash
aws secretsmanager get-random-password \
    [--password-length <value>] \
    [--exclude-characters <value>] \
    [--exclude-numbers | --no-exclude-numbers] \
    [--exclude-punctuation | --no-exclude-punctuation] \
    [--exclude-uppercase | --no-exclude-uppercase] \
    [--exclude-lowercase | --no-exclude-lowercase] \
    [--include-space | --no-include-space] \
    [--require-each-included-type | --no-require-each-included-type] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--password-length` | No | long | 32 | Length of the password (1-4096) |
| `--exclude-characters` | No | string | None | Characters to exclude (max 4096 chars) |
| `--exclude-numbers` | No | boolean | false | Exclude digits 0-9 |
| `--exclude-punctuation` | No | boolean | false | Exclude ``!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~`` |
| `--exclude-uppercase` | No | boolean | false | Exclude uppercase A-Z |
| `--exclude-lowercase` | No | boolean | false | Exclude lowercase a-z |
| `--include-space` | No | boolean | false | Include space character |
| `--require-each-included-type` | No | boolean | false | Require at least one of each included character type |

**Output Schema:**
```json
{
    "RandomPassword": "string"
}
```

---
