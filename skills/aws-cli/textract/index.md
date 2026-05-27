# AWS CLI v2 -- Textract Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/textract/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `detect-document-text` | Synchronous | Detect text in a document (PAGE, LINE, WORD blocks) |
| `analyze-document` | Synchronous | Analyze document for tables, forms, queries, signatures, layout |
| `analyze-expense` | Synchronous | Analyze invoices and receipts |
| `analyze-id` | Synchronous | Analyze identity documents (driver licenses, passports) |
| `start-document-analysis` | Asynchronous | Start async document analysis job |
| `start-document-text-detection` | Asynchronous | Start async text detection job |
| `start-expense-analysis` | Asynchronous | Start async expense analysis job |
| `start-lending-analysis` | Asynchronous | Start async lending document analysis job |
| `get-document-analysis` | Asynchronous | Get results of async document analysis |
| `get-document-text-detection` | Asynchronous | Get results of async text detection |
| `get-expense-analysis` | Asynchronous | Get results of async expense analysis |
| `get-lending-analysis` | Asynchronous | Get results of async lending analysis |
| `get-lending-analysis-summary` | Asynchronous | Get summary of async lending analysis |
| `create-adapter` | Adapter | Create a custom adapter |
| `create-adapter-version` | Adapter | Create a new version of an adapter |
| `delete-adapter` | Adapter | Delete an adapter |
| `delete-adapter-version` | Adapter | Delete a specific adapter version |
| `get-adapter` | Adapter | Get adapter details |
| `get-adapter-version` | Adapter | Get details of an adapter version |
| `list-adapters` | Adapter | List all adapters |
| `list-adapter-versions` | Adapter | List versions of an adapter |
| `update-adapter` | Adapter | Update adapter configuration |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws textract` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Document Input Structure (Synchronous)
Synchronous operations accept a `--document` parameter with either inline bytes or an S3 reference:
```json
{
    "Bytes": "base64-encoded-bytes",
    "S3Object": {
        "Bucket": "string",
        "Name": "string",
        "Version": "string"
    }
}
```
- Supports JPEG, PNG, PDF (single-page), TIFF formats
- Max size: 5 MB for synchronous operations

### Document Location Structure (Asynchronous)
Asynchronous operations accept a `--document-location` parameter with an S3 reference:
```json
{
    "S3Object": {
        "Bucket": "string",
        "Name": "string",
        "Version": "string"
    }
}
```
- Supports multi-page PDF and TIFF for asynchronous operations

### Block Types
| BlockType | Description |
|-----------|-------------|
| `PAGE` | A page of the document |
| `LINE` | A string of space-delimited contiguous words |
| `WORD` | One or more characters not separated by spaces |
| `KEY_VALUE_SET` | A key-value pair in a form |
| `TABLE` | A detected table |
| `CELL` | A cell within a table |
| `MERGED_CELL` | A merged cell within a table |
| `SELECTION_ELEMENT` | A checkbox or radio button |
| `SIGNATURE` | A detected signature |
| `QUERY` | A query that was asked |
| `QUERY_RESULT` | The answer to a query |
| `LAYOUT_TEXT` | Body text in the layout |
| `LAYOUT_TITLE` | A title in the layout |
| `LAYOUT_HEADER` | A header in the layout |
| `LAYOUT_FOOTER` | A footer in the layout |
| `LAYOUT_SECTION_HEADER` | A section header |
| `LAYOUT_PAGE_NUMBER` | A page number |
| `LAYOUT_LIST` | A list in the layout |
| `LAYOUT_FIGURE` | A figure in the layout |
| `LAYOUT_TABLE` | A table in the layout |
| `LAYOUT_KEY_VALUE` | A key-value in the layout |

### Async Job Status Values
| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Job is still processing |
| `SUCCEEDED` | Job completed successfully |
| `FAILED` | Job failed |
| `PARTIAL_SUCCESS` | Job completed with partial results |

### Feature Types
| Feature | Description |
|---------|-------------|
| `TABLES` | Detect tables and cells |
| `FORMS` | Detect key-value pairs |
| `QUERIES` | Answer specific questions about the document |
| `SIGNATURES` | Detect signatures |
| `LAYOUT` | Detect document layout structure |
