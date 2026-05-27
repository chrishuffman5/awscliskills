# Lexicons

Pronunciation lexicons use the W3C Pronunciation Lexicon Specification (PLS) format to customize how words are pronounced during speech synthesis.

---

### 2.1 `put-lexicon`

Creates or updates a pronunciation lexicon. If a lexicon with the same name exists, it is replaced.

**Synopsis:**
```bash
aws polly put-lexicon \
    --name <value> \
    --content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Lexicon name (1-20 alphanumeric chars, pattern: `[0-9A-Za-z]{1,20}`) |
| `--content` | **Yes** | string | -- | PLS lexicon content as string or `file://` path |

**Output:** None (HTTP 200 on success)

**Example PLS lexicon file (lexicon.pls):**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<lexicon version="1.0"
    xmlns="http://www.w3.org/2005/01/pronunciation-lexicon"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.w3.org/2005/01/pronunciation-lexicon
        http://www.w3.org/TR/2007/CR-pronunciation-lexicon-20071212/pls.xsd"
    alphabet="ipa" xml:lang="en-US">
  <lexeme>
    <grapheme>AWS</grapheme>
    <alias>Amazon Web Services</alias>
  </lexeme>
</lexicon>
```

---

### 2.2 `get-lexicon`

Retrieves a pronunciation lexicon and its attributes.

**Synopsis:**
```bash
aws polly get-lexicon \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the lexicon (1-20 alphanumeric chars) |

**Output Schema:**
```json
{
    "Lexicon": {
        "Content": "string",
        "Name": "string"
    },
    "LexiconAttributes": {
        "Alphabet": "ipa|x-sampa",
        "LanguageCode": "string",
        "LastModified": "timestamp",
        "LexiconArn": "string",
        "LexemesCount": "integer",
        "Size": "integer"
    }
}
```

---

### 2.3 `delete-lexicon`

Deletes a pronunciation lexicon.

**Synopsis:**
```bash
aws polly delete-lexicon \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the lexicon to delete (1-20 alphanumeric chars) |

**Output:** None (HTTP 200 on success)

---

### 2.4 `list-lexicons`

Lists all pronunciation lexicons in the region. **Paginated operation.**

**Synopsis:**
```bash
aws polly list-lexicons \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Lexicons": [
        {
            "Name": "string",
            "Attributes": {
                "Alphabet": "ipa|x-sampa",
                "LanguageCode": "string",
                "LastModified": "timestamp",
                "LexiconArn": "string",
                "LexemesCount": "integer",
                "Size": "integer"
            }
        }
    ],
    "NextToken": "string"
}
```
