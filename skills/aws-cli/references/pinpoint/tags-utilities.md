# Tags & Utilities

### 11.1 `tag-resource`

Adds tags to a Pinpoint resource.

**Synopsis:**
```bash
aws pinpoint tag-resource \
    --resource-arn <value> \
    --tags-model <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags-model` | **Yes** | structure | -- | Tags. Shorthand: `tags={Key1=Value1,Key2=Value2}` |

**Output:** None

---

### 11.2 `untag-resource`

Removes tags from a Pinpoint resource.

**Synopsis:**
```bash
aws pinpoint untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove. Space-separated |

**Output:** None

---

### 11.3 `list-tags-for-resource`

Lists tags for a Pinpoint resource.

**Synopsis:**
```bash
aws pinpoint list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "TagsModel": {
        "tags": {"string": "string"}
    }
}
```

---

### 11.4 `phone-number-validate`

Returns information about a phone number.

**Synopsis:**
```bash
aws pinpoint phone-number-validate \
    --number-validate-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--number-validate-request` | **Yes** | structure | -- | Shorthand: `PhoneNumber=string` or `IsoCountryCode=string,PhoneNumber=string` |

**Output Schema:**
```json
{
    "NumberValidateResponse": {
        "Carrier": "string",
        "City": "string",
        "CleansedPhoneNumberE164": "string",
        "CleansedPhoneNumberNational": "string",
        "Country": "string",
        "CountryCodeIso2": "string",
        "CountryCodeNumeric": "string",
        "County": "string",
        "OriginalCountryCodeIso2": "string",
        "OriginalPhoneNumber": "string",
        "PhoneType": "string",
        "PhoneTypeCode": "integer",
        "Timezone": "string",
        "ZipCode": "string"
    }
}
```

---

### 11.5 `remove-attributes`

Removes one or more custom attributes (by attribute name) from all endpoints associated with an application.

**Synopsis:**
```bash
aws pinpoint remove-attributes \
    --application-id <value> \
    --attribute-type <value> \
    --update-attributes-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--attribute-type` | **Yes** | string | -- | Attribute type: `endpoint-custom-attributes`, `endpoint-user-attributes`, `endpoint-metrics` |
| `--update-attributes-request` | **Yes** | structure | -- | Contains `Blacklist` (list of attribute names to remove) |

**Output Schema:**
```json
{
    "AttributesResource": {
        "ApplicationId": "string",
        "AttributeType": "string",
        "Attributes": ["string"]
    }
}
```
