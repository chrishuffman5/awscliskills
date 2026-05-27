# VPC Peering

### 12.1 `create-vpc-peering-authorization`

Authorizes a VPC in another AWS account to create a peering connection with a GameLift fleet VPC.

**Synopsis:**
```bash
aws gamelift create-vpc-peering-authorization \
    --game-lift-aws-account-id <value> \
    --peer-vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-lift-aws-account-id` | **Yes** | string | -- | AWS account ID with the GameLift fleet (1-1024 chars) |
| `--peer-vpc-id` | **Yes** | string | -- | VPC ID to authorize peering with (1-1024 chars) |

**Output Schema:**
```json
{
    "VpcPeeringAuthorization": {
        "GameLiftAwsAccountId": "string",
        "PeerVpcAwsAccountId": "string",
        "PeerVpcId": "string",
        "CreationTime": "timestamp",
        "ExpirationTime": "timestamp"
    }
}
```

---

### 12.2 `delete-vpc-peering-authorization`

Cancels a VPC peering authorization.

**Synopsis:**
```bash
aws gamelift delete-vpc-peering-authorization \
    --game-lift-aws-account-id <value> \
    --peer-vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-lift-aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--peer-vpc-id` | **Yes** | string | -- | VPC ID |

**Output Schema:**
```json
None
```

---

### 12.3 `describe-vpc-peering-authorizations`

Retrieves all VPC peering authorizations in the account.

**Synopsis:**
```bash
aws gamelift describe-vpc-peering-authorizations \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| (none) | -- | -- | -- | No parameters required |

**Output Schema:**
```json
{
    "VpcPeeringAuthorizations": [
        {
            "GameLiftAwsAccountId": "string",
            "PeerVpcAwsAccountId": "string",
            "PeerVpcId": "string",
            "CreationTime": "timestamp",
            "ExpirationTime": "timestamp"
        }
    ]
}
```

---

### 12.4 `create-vpc-peering-connection`

Establishes a VPC peering connection between a GameLift fleet VPC and a VPC in another account.

**Synopsis:**
```bash
aws gamelift create-vpc-peering-connection \
    --fleet-id <value> \
    --peer-vpc-aws-account-id <value> \
    --peer-vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--peer-vpc-aws-account-id` | **Yes** | string | -- | AWS account ID owning the peer VPC (1-1024 chars) |
| `--peer-vpc-id` | **Yes** | string | -- | VPC ID to peer with (1-1024 chars) |

**Output Schema:**
```json
None
```

---

### 12.5 `delete-vpc-peering-connection`

Removes a VPC peering connection.

**Synopsis:**
```bash
aws gamelift delete-vpc-peering-connection \
    --fleet-id <value> \
    --vpc-peering-connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--vpc-peering-connection-id` | **Yes** | string | -- | VPC peering connection ID (1-1024 chars) |

**Output Schema:**
```json
None
```

---

### 12.6 `describe-vpc-peering-connections`

Retrieves all VPC peering connections for GameLift fleets.

**Synopsis:**
```bash
aws gamelift describe-vpc-peering-connections \
    [--fleet-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | No | string | None | Filter by fleet (omit for all) |

**Output Schema:**
```json
{
    "VpcPeeringConnections": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "IpV4CidrBlock": "string",
            "VpcPeeringConnectionId": "string",
            "Status": {
                "Code": "string",
                "Message": "string"
            },
            "PeerVpcId": "string",
            "GameLiftVpcId": "string"
        }
    ]
}
```
