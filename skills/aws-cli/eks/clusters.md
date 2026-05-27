# Clusters

### 1.1 `create-cluster`

Creates an Amazon EKS control plane.

**Synopsis:**
```bash
aws eks create-cluster \
    --name <value> \
    --role-arn <value> \
    --resources-vpc-config <value> \
    [--kubernetes-version <value>] \
    [--kubernetes-network-config <value>] \
    [--logging <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--encryption-config <value>] \
    [--outpost-config <value>] \
    [--access-config <value>] \
    [--bootstrap-self-managed-addons | --no-bootstrap-self-managed-addons] \
    [--upgrade-policy <value>] \
    [--zonal-shift-config <value>] \
    [--remote-network-config <value>] \
    [--compute-config <value>] \
    [--storage-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name (1-100 chars, alphanumeric, hyphens, underscores) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for the cluster |
| `--resources-vpc-config` | **Yes** | structure | -- | VPC config. Shorthand: `subnetIds=string,string,securityGroupIds=string,endpointPublicAccess=boolean,endpointPrivateAccess=boolean,publicAccessCidrs=string` |
| `--kubernetes-version` | No | string | latest | Kubernetes version (e.g., `1.29`) |
| `--kubernetes-network-config` | No | structure | None | Network config. Shorthand: `serviceIpv4Cidr=string,ipFamily=ipv4\|ipv6` |
| `--logging` | No | structure | None | Control plane logging. JSON: `{"clusterLogging":[{"types":["api","audit","authenticator","controllerManager","scheduler"],"enabled":true}]}` |
| `--client-request-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags as key=value pairs |
| `--encryption-config` | No | list | None | Encryption config. Shorthand: `resources=string,provider={keyArn=string}` |
| `--outpost-config` | No | structure | None | Outpost configuration |
| `--access-config` | No | structure | None | Access config. Shorthand: `bootstrapClusterCreatorAdminPermissions=boolean,authenticationMode=CONFIG_MAP\|API\|API_AND_CONFIG_MAP` |
| `--bootstrap-self-managed-addons` | No | boolean | true | Bootstrap self-managed add-ons (vpc-cni, kube-proxy, coredns) |
| `--upgrade-policy` | No | structure | None | Upgrade policy. Shorthand: `supportType=STANDARD\|EXTENDED` |
| `--zonal-shift-config` | No | structure | None | Zonal shift config. Shorthand: `enabled=boolean` |
| `--compute-config` | No | structure | None | Auto Mode compute config |
| `--storage-config` | No | structure | None | Auto Mode storage config |

**Output Schema:**
```json
{
    "cluster": {
        "name": "string",
        "arn": "string",
        "createdAt": "timestamp",
        "version": "string",
        "endpoint": "string",
        "roleArn": "string",
        "resourcesVpcConfig": {
            "subnetIds": ["string"],
            "securityGroupIds": ["string"],
            "clusterSecurityGroupId": "string",
            "vpcId": "string",
            "endpointPublicAccess": true|false,
            "endpointPrivateAccess": true|false,
            "publicAccessCidrs": ["string"]
        },
        "kubernetesNetworkConfig": {
            "serviceIpv4Cidr": "string",
            "serviceIpv6Cidr": "string",
            "ipFamily": "ipv4|ipv6"
        },
        "logging": {
            "clusterLogging": [
                {
                    "types": ["api", "audit", "authenticator", "controllerManager", "scheduler"],
                    "enabled": true|false
                }
            ]
        },
        "identity": {
            "oidc": {
                "issuer": "string"
            }
        },
        "status": "CREATING|ACTIVE|DELETING|FAILED|UPDATING|PENDING",
        "certificateAuthority": {
            "data": "string"
        },
        "platformVersion": "string",
        "tags": {"string": "string"},
        "encryptionConfig": [],
        "accessConfig": {
            "bootstrapClusterCreatorAdminPermissions": true|false,
            "authenticationMode": "CONFIG_MAP|API|API_AND_CONFIG_MAP"
        },
        "upgradePolicy": {
            "supportType": "STANDARD|EXTENDED"
        }
    }
}
```

---

### 1.2 `delete-cluster`

Deletes the Amazon EKS cluster. Must delete all node groups and Fargate profiles first.

**Synopsis:**
```bash
aws eks delete-cluster \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |

**Output Schema:**
```json
{
    "cluster": {
        "name": "string",
        "arn": "string",
        "status": "DELETING",
        "version": "string",
        "endpoint": "string",
        "roleArn": "string"
    }
}
```

---

### 1.3 `describe-cluster`

Returns descriptive information about an Amazon EKS cluster.

**Synopsis:**
```bash
aws eks describe-cluster \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |

**Output Schema:** Same as `create-cluster` output (full cluster object).

---

### 1.4 `list-clusters`

Lists the Amazon EKS clusters in your account. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-clusters \
    [--include <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include` | No | list(string) | None | Include clusters by connector type |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "clusters": ["string"],
    "nextToken": "string"
}
```

---

### 1.5 `update-cluster-config`

Updates an Amazon EKS cluster configuration (logging, VPC access, encryption, access config).

**Synopsis:**
```bash
aws eks update-cluster-config \
    --name <value> \
    [--resources-vpc-config <value>] \
    [--logging <value>] \
    [--client-request-token <value>] \
    [--access-config <value>] \
    [--upgrade-policy <value>] \
    [--zonal-shift-config <value>] \
    [--compute-config <value>] \
    [--storage-config <value>] \
    [--kubernetes-network-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |
| `--resources-vpc-config` | No | structure | None | Updated VPC config |
| `--logging` | No | structure | None | Updated logging config |
| `--client-request-token` | No | string | None | Idempotency token |
| `--access-config` | No | structure | None | Updated access config |
| `--upgrade-policy` | No | structure | None | Updated upgrade policy |

**Output Schema:**
```json
{
    "update": {
        "id": "string",
        "status": "InProgress|Failed|Cancelled|Successful",
        "type": "ConfigUpdate",
        "params": [
            {
                "type": "string",
                "value": "string"
            }
        ],
        "createdAt": "timestamp",
        "errors": [
            {
                "errorCode": "string",
                "errorMessage": "string",
                "resourceIds": ["string"]
            }
        ]
    }
}
```

---

### 1.6 `update-cluster-version`

Updates the Kubernetes version for an Amazon EKS cluster.

**Synopsis:**
```bash
aws eks update-cluster-version \
    --name <value> \
    --kubernetes-version <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |
| `--kubernetes-version` | **Yes** | string | -- | Target Kubernetes version |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:** Same update object as `update-cluster-config`.

---

### 1.7 `update-kubeconfig`

Configures kubectl to communicate with an Amazon EKS cluster by updating or creating a kubeconfig file.

**Synopsis:**
```bash
aws eks update-kubeconfig \
    --name <value> \
    [--kubeconfig <value>] \
    [--role-arn <value>] \
    [--dry-run] \
    [--verbose] \
    [--alias <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |
| `--kubeconfig` | No | string | `~/.kube/config` | Kubeconfig file path |
| `--role-arn` | No | string | None | IAM role ARN to assume for cluster auth |
| `--dry-run` | No | boolean | false | Print kubeconfig without writing |
| `--verbose` | No | boolean | false | Print more detailed output |
| `--alias` | No | string | cluster ARN | Alias for the cluster context |

**Output:** Prints status message indicating the kubeconfig was updated.

---

### 1.8 `describe-cluster-versions`

Lists available Kubernetes versions for EKS clusters, with optional filtering.

**Synopsis:**
```bash
aws eks describe-cluster-versions \
    [--cluster-type <value>] \
    [--default-only | --no-default-only] \
    [--include-all | --no-include-all] \
    [--cluster-versions-only | --no-cluster-versions-only] \
    [--status <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-type` | No | string | None | Filter by cluster type |
| `--default-only` | No | boolean | false | Only return the default version |
| `--include-all` | No | boolean | false | Include all versions including deprecated |
| `--cluster-versions-only` | No | boolean | false | Return only version strings |
| `--status` | No | string | None | Filter by version status |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "clusterVersions": [
        {
            "clusterVersion": "string",
            "clusterType": "string",
            "defaultPlatformVersion": "string",
            "defaultVersion": true,
            "releaseDate": "timestamp",
            "endOfStandardSupportDate": "timestamp",
            "endOfExtendedSupportDate": "timestamp",
            "status": "string",
            "kubernetesPatchVersion": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.9 `register-cluster`

Registers an external Kubernetes cluster with Amazon EKS to enable EKS Connector.

**Synopsis:**
```bash
aws eks register-cluster \
    --name <value> \
    --connector-config <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name for the connected cluster |
| `--connector-config` | **Yes** | structure | -- | Connector configuration. Shorthand: `roleArn=string,provider=EKS_ANYWHERE\|ANTHOS\|GKE\|AKS\|OPENSHIFT\|TANZU\|RANCHER\|EC2\|OTHER` |
| `--client-request-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "cluster": {
        "name": "string",
        "arn": "string",
        "status": "PENDING",
        "connectorConfig": {
            "activationId": "string",
            "activationCode": "string",
            "activationExpiry": "timestamp",
            "provider": "string",
            "roleArn": "string"
        },
        "tags": {"key": "value"}
    }
}
```

---

### 1.10 `deregister-cluster`

Deregisters a connected cluster from Amazon EKS.

**Synopsis:**
```bash
aws eks deregister-cluster \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connected cluster name |

**Output Schema:**
```json
{
    "cluster": {
        "name": "string",
        "arn": "string",
        "status": "DELETING",
        "connectorConfig": {
            "provider": "string",
            "roleArn": "string"
        }
    }
}
```

---

### 1.11 `get-token`

Gets a token for authentication with an Amazon EKS cluster. Used by kubectl and other Kubernetes clients.

**Synopsis:**
```bash
aws eks get-token \
    --cluster-name <value> \
    [--role-arn <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--role-arn` | No | string | None | IAM role ARN to assume for authentication |

**Output Schema:**
```json
{
    "kind": "ExecCredential",
    "apiVersion": "client.authentication.k8s.io/v1beta1",
    "spec": {},
    "status": {
        "expirationTimestamp": "timestamp",
        "token": "string"
    }
}
```
