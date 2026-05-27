# SBOM Scan

> This command uses the `aws inspector-scan` namespace, not `aws inspector2`.

### 11.1 `scan-sbom`

Scans a provided Software Bill of Materials (SBOM) for security vulnerabilities. The SBOM must be in CycloneDX 1.5 format and is limited to 2000 components.

**Synopsis:**
```bash
aws inspector-scan scan-sbom \
    --sbom <value> \
    [--output-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sbom` | **Yes** | document | -- | The SBOM to scan in CycloneDX 1.5 JSON format. Can be inline JSON or `file://path` |
| `--output-format` | No | string | None | Output format: `CYCLONE_DX_1_5`, `INSPECTOR`, `INSPECTOR_ALT` |

**Output Schema:**
```json
{
    "sbom": {
        "...": "document - vulnerability report"
    }
}
```

The output `sbom` field is a document type containing the vulnerability report with NVD and CVSS scores when available. The format varies based on the `--output-format` parameter:

- **`CYCLONE_DX_1_5`**: Returns results in CycloneDX 1.5 format with vulnerabilities added
- **`INSPECTOR`**: Returns results in Amazon Inspector format
- **`INSPECTOR_ALT`**: Returns results in Amazon Inspector alternative format

**Example:**
```bash
# Scan an SBOM file
aws inspector-scan scan-sbom \
    --sbom file://my-sbom.json \
    --output-format CYCLONE_DX_1_5

# Scan with inline SBOM
aws inspector-scan scan-sbom \
    --sbom '{"bomFormat":"CycloneDX","specVersion":"1.5","components":[{"type":"library","name":"log4j-core","version":"2.14.1","purl":"pkg:maven/org.apache.logging.log4j/log4j-core@2.14.1"}]}'
```
