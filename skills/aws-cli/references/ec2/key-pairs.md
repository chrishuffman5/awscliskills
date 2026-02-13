# Key Pairs

### 4.1 `aws ec2 create-key-pair`

**Description:** Creates an ED25519 or 2048-bit RSA key pair. EC2 stores the public key and returns the private key as unencrypted PEM or PPK. Limit: 5,000 per region.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--key-name` | string | **Required** | Unique name (max 255 ASCII chars) |
| `--key-type` | string | Optional | `rsa` (default) or `ed25519`. ED25519 not supported for Windows |
| `--key-format` | string | Optional | `pem` (default) or `ppk` (PuTTY) |
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "KeyPairId": "string",
  "KeyName": "string",
  "KeyFingerprint": "string",
  "KeyMaterial": "string",
  "Tags": [{ "Key": "string", "Value": "string" }]
}
```

- `KeyMaterial` -- Unencrypted PEM-encoded private key (only returned at creation time)
- `KeyFingerprint` -- SHA-1 digest (RSA) or base64-encoded SHA-256 (ED25519)

---

### 4.2 `aws ec2 delete-key-pair`

**Description:** Deletes a key pair by removing the public key from EC2.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--key-name` | string | Optional | Key pair name |
| `--key-pair-id` | string | Optional | Key pair ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "Return": true,
  "KeyPairId": "string"
}
```

---

### 4.3 `aws ec2 describe-key-pairs`

**Description:** Describes specified or all key pairs.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--key-names` | list(string) | Optional | Key pair names |
| `--key-pair-ids` | list(string) | Optional | Key pair IDs |
| `--include-public-key` / `--no-include-public-key` | boolean | Optional | Include public key material (default: false) |
| `--filters` | list(structure) | Optional | Filters: `key-pair-id`, `fingerprint`, `key-name`, `tag:<key>`, `tag-key` |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "KeyPairs": [
    {
      "KeyPairId": "string",
      "KeyName": "string",
      "KeyType": "rsa|ed25519",
      "KeyFingerprint": "string",
      "CreateTime": "timestamp",
      "PublicKey": "string",
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ]
}
```

---

### 4.4 `aws ec2 import-key-pair`

**Description:** Imports the public key from a key pair you created with a third-party tool. Only the public key is transferred.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--key-name` | string | **Required** | Unique name for the key pair |
| `--public-key-material` | blob | **Required** | The public key (use `fileb://path`) |
| `--tag-specifications` | list(structure) | Optional | Tags on import |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "KeyFingerprint": "string",
  "KeyName": "string",
  "KeyPairId": "string",
  "Tags": [{ "Key": "string", "Value": "string" }]
}
```

---

