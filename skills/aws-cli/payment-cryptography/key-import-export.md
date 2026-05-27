# Key Import/Export

### 2.1 `import-key`

Imports a key into AWS Payment Cryptography. Supports multiple import methods: root/trusted certificate, TR-31, TR-34, key cryptogram, and ECDH.

**Synopsis:**
```bash
aws payment-cryptography import-key \
    --key-material <value> \
    [--key-check-value-algorithm <value>] \
    [--enabled | --no-enabled] \
    [--tags <value>] \
    [--replication-regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-material` | **Yes** | tagged union | -- | Key material to import (one of the structures below) |
| `--key-check-value-algorithm` | No | string | None | KCV algorithm: `CMAC`, `ANSI_X9_24`, `HMAC`, `SHA_1` |
| `--enabled` / `--no-enabled` | No | boolean | true | Enable key after import |
| `--tags` | No | list | None | Tags (max 200) |
| `--replication-regions` | No | list(string) | None | AWS Regions for replication |

**Key Material Options (tagged union -- specify one):**

**RootCertificatePublicKey:**
```json
{
    "RootCertificatePublicKey": {
        "KeyAttributes": { "KeyUsage": "string", "KeyClass": "string", "KeyAlgorithm": "string", "KeyModesOfUse": {} },
        "PublicKeyCertificate": "string"
    }
}
```

**TrustedCertificatePublicKey:**
```json
{
    "TrustedCertificatePublicKey": {
        "KeyAttributes": { "KeyUsage": "string", "KeyClass": "string", "KeyAlgorithm": "string", "KeyModesOfUse": {} },
        "CertificateAuthorityPublicKeyIdentifier": "string",
        "PublicKeyCertificate": "string"
    }
}
```

**Tr31KeyBlock:**
```json
{
    "Tr31KeyBlock": {
        "WrappingKeyIdentifier": "string",
        "WrappedKeyBlock": "string"
    }
}
```

**Tr34KeyBlock:**
```json
{
    "Tr34KeyBlock": {
        "CertificateAuthorityPublicKeyIdentifier": "string",
        "SigningKeyCertificate": "string",
        "ImportToken": "string",
        "WrappedKeyBlock": "string",
        "KeyBlockFormat": "X9_TR34_2012",
        "RandomNonce": "string"
    }
}
```

**KeyCryptogram:**
```json
{
    "KeyCryptogram": {
        "KeyAttributes": {},
        "Exportable": "boolean",
        "WrappedKeyCryptogram": "string",
        "ImportToken": "string",
        "WrappingSpec": "RSA_OAEP_SHA_256|RSA_OAEP_SHA_512"
    }
}
```

**DiffieHellmanTr31KeyBlock:**
```json
{
    "DiffieHellmanTr31KeyBlock": {
        "PrivateKeyIdentifier": "string",
        "CertificateAuthorityPublicKeyIdentifier": "string",
        "PublicKeyCertificate": "string",
        "DeriveKeyAlgorithm": "string",
        "KeyDerivationFunction": "NIST_SP800|ANSI_X963",
        "KeyDerivationHashAlgorithm": "SHA_256|SHA_384|SHA_512",
        "DerivationData": { "SharedInformation": "string" },
        "WrappedKeyBlock": "string"
    }
}
```

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {},
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": "boolean",
        "Exportable": "boolean",
        "KeyState": "string",
        "KeyOrigin": "EXTERNAL",
        "CreateTimestamp": "timestamp",
        "MultiRegionKeyType": "string",
        "ReplicationStatus": {}
    }
}
```

---

### 2.2 `export-key`

Exports a key from AWS Payment Cryptography. Supports TR-31, TR-34, key cryptogram, ECDH, and AS2805 export methods.

**Synopsis:**
```bash
aws payment-cryptography export-key \
    --key-material <value> \
    --export-key-identifier <value> \
    [--export-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-material` | **Yes** | tagged union | -- | Export method and wrapping parameters |
| `--export-key-identifier` | **Yes** | string | -- | KeyARN or alias of the key to export |
| `--export-attributes` | No | structure | None | DUKPT IPEK generation attributes and KCV algorithm |

**Key Material Options (tagged union -- specify one):**

**Tr31KeyBlock:** `{ "WrappingKeyIdentifier": "string", "KeyBlockHeaders": {} }`

**Tr34KeyBlock:** `{ "CertificateAuthorityPublicKeyIdentifier": "string", "WrappingKeyCertificate": "string", "KeyBlockFormat": "X9_TR34_2012", "ExportToken": "string", ... }`

**KeyCryptogram:** `{ "CertificateAuthorityPublicKeyIdentifier": "string", "WrappingKeyCertificate": "string", "WrappingSpec": "RSA_OAEP_SHA_256|RSA_OAEP_SHA_512" }`

**DiffieHellmanTr31KeyBlock:** `{ "PrivateKeyIdentifier": "string", "CertificateAuthorityPublicKeyIdentifier": "string", "PublicKeyCertificate": "string", "DeriveKeyAlgorithm": "string", "KeyDerivationFunction": "string", "KeyDerivationHashAlgorithm": "string", "DerivationData": {}, "KeyBlockHeaders": {} }`

**As2805KeyCryptogram:** `{ "WrappingKeyIdentifier": "string", "As2805KeyVariant": "VARIANT_MASK_82C0|..." }`

**Output Schema:**
```json
{
    "WrappedKey": {
        "WrappingKeyArn": "string",
        "WrappedKeyMaterialFormat": "TR34_KEY_BLOCK|TR31_KEY_BLOCK|KEY_CRYPTOGRAM",
        "KeyMaterial": "string",
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string"
    }
}
```

---

### 2.3 `get-parameters-for-import`

Gets the parameters required for key import, including an import token and wrapping key certificate.

**Synopsis:**
```bash
aws payment-cryptography get-parameters-for-import \
    --key-material-type <value> \
    --wrapping-key-algorithm <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-material-type` | **Yes** | string | -- | Import method: `TR34_KEY_BLOCK`, `TR31_KEY_BLOCK`, `ROOT_PUBLIC_KEY_CERTIFICATE`, `TRUSTED_PUBLIC_KEY_CERTIFICATE`, `KEY_CRYPTOGRAM` |
| `--wrapping-key-algorithm` | **Yes** | string | -- | Wrapping key algorithm (e.g., `RSA_2048`, `AES_256`) |

**Output Schema:**
```json
{
    "ImportToken": "string",
    "ParametersValidUntilTimestamp": "timestamp",
    "WrappingKeyAlgorithm": "string",
    "WrappingKeyCertificate": "string",
    "WrappingKeyCertificateChain": "string"
}
```

---

### 2.4 `get-parameters-for-export`

Gets the parameters required for key export, including an export token and signing key certificate.

**Synopsis:**
```bash
aws payment-cryptography get-parameters-for-export \
    --key-material-type <value> \
    --signing-key-algorithm <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-material-type` | **Yes** | string | -- | Export method: `TR34_KEY_BLOCK`, `TR31_KEY_BLOCK`, `ROOT_PUBLIC_KEY_CERTIFICATE`, `TRUSTED_PUBLIC_KEY_CERTIFICATE`, `KEY_CRYPTOGRAM` |
| `--signing-key-algorithm` | **Yes** | string | -- | Signing key algorithm (e.g., `RSA_2048`) |

**Output Schema:**
```json
{
    "ExportToken": "string",
    "ParametersValidUntilTimestamp": "timestamp",
    "SigningKeyAlgorithm": "string",
    "SigningKeyCertificate": "string",
    "SigningKeyCertificateChain": "string"
}
```
