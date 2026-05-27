# AWS CLI v2 -- EKS (Elastic Kubernetes Service) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/eks/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Cluster | Create an EKS cluster |
| `delete-cluster` | Cluster | Delete an EKS cluster |
| `describe-cluster` | Cluster | Describe an EKS cluster |
| `list-clusters` | Cluster | List EKS clusters |
| `update-cluster-config` | Cluster | Update cluster configuration |
| `update-cluster-version` | Cluster | Update Kubernetes version |
| `update-kubeconfig` | Cluster | Update local kubeconfig |
| `create-nodegroup` | Node Group | Create a managed node group |
| `delete-nodegroup` | Node Group | Delete a managed node group |
| `describe-nodegroup` | Node Group | Describe a managed node group |
| `list-nodegroups` | Node Group | List managed node groups |
| `update-nodegroup-config` | Node Group | Update node group configuration |
| `update-nodegroup-version` | Node Group | Update node group AMI version |
| `create-fargate-profile` | Fargate | Create a Fargate profile |
| `delete-fargate-profile` | Fargate | Delete a Fargate profile |
| `describe-fargate-profile` | Fargate | Describe a Fargate profile |
| `list-fargate-profiles` | Fargate | List Fargate profiles |
| `create-addon` | Add-on | Install an EKS add-on |
| `delete-addon` | Add-on | Delete an EKS add-on |
| `describe-addon` | Add-on | Describe an EKS add-on |
| `describe-addon-versions` | Add-on | List available add-on versions |
| `describe-addon-configuration` | Add-on | Describe add-on configuration schema |
| `list-addons` | Add-on | List installed add-ons |
| `update-addon` | Add-on | Update an EKS add-on |
| `create-access-entry` | Access | Create an access entry |
| `delete-access-entry` | Access | Delete an access entry |
| `describe-access-entry` | Access | Describe an access entry |
| `list-access-entries` | Access | List access entries |
| `update-access-entry` | Access | Update an access entry |
| `associate-access-policy` | Access | Associate an access policy |
| `disassociate-access-policy` | Access | Disassociate an access policy |
| `list-associated-access-policies` | Access | List associated access policies |
| `list-access-policies` | Access | List available access policies |
| `associate-identity-provider-config` | Identity | Associate an OIDC identity provider |
| `disassociate-identity-provider-config` | Identity | Disassociate an identity provider |
| `describe-identity-provider-config` | Identity | Describe an identity provider config |
| `list-identity-provider-configs` | Identity | List identity provider configs |
| `create-pod-identity-association` | Pod Identity | Create a Pod Identity association |
| `delete-pod-identity-association` | Pod Identity | Delete a Pod Identity association |
| `describe-pod-identity-association` | Pod Identity | Describe a Pod Identity association |
| `list-pod-identity-associations` | Pod Identity | List Pod Identity associations |
| `update-pod-identity-association` | Pod Identity | Update a Pod Identity association |
| `associate-encryption-config` | Encryption | Associate encryption config |
| `describe-insight` | Insights | Describe a cluster insight |
| `list-insights` | Insights | List cluster insights |
| `describe-cluster-versions` | Capabilities | List available Kubernetes versions |
| `create-eks-anywhere-subscription` | EKS Anywhere | Create an EKS Anywhere subscription |
| `delete-eks-anywhere-subscription` | EKS Anywhere | Delete an EKS Anywhere subscription |
| `describe-eks-anywhere-subscription` | EKS Anywhere | Describe an EKS Anywhere subscription |
| `list-eks-anywhere-subscriptions` | EKS Anywhere | List EKS Anywhere subscriptions |
| `update-eks-anywhere-subscription` | EKS Anywhere | Update an EKS Anywhere subscription |
| `describe-update` | Updates | Describe an update |
| `list-updates` | Updates | List updates for a resource |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws eks` commands.

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

### Cluster Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Cluster is being created |
| `ACTIVE` | Cluster is running |
| `DELETING` | Cluster is being deleted |
| `FAILED` | Cluster creation failed |
| `UPDATING` | Cluster is being updated |
| `PENDING` | Cluster is pending |

### Node Group Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Node group is being created |
| `ACTIVE` | Node group is active |
| `UPDATING` | Node group is being updated |
| `DELETING` | Node group is being deleted |
| `CREATE_FAILED` | Node group creation failed |
| `DELETE_FAILED` | Node group deletion failed |
| `DEGRADED` | Node group is degraded |

### Add-on Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Add-on is being created |
| `ACTIVE` | Add-on is active |
| `CREATE_FAILED` | Add-on creation failed |
| `UPDATING` | Add-on is being updated |
| `DELETING` | Add-on is being deleted |
| `DELETE_FAILED` | Add-on deletion failed |
| `DEGRADED` | Add-on is degraded |

### Common EKS Add-ons
| Add-on | Description |
|--------|-------------|
| `vpc-cni` | Amazon VPC CNI plugin for pod networking |
| `coredns` | CoreDNS for Kubernetes DNS |
| `kube-proxy` | Kubernetes network proxy |
| `aws-ebs-csi-driver` | Amazon EBS CSI driver |
| `aws-efs-csi-driver` | Amazon EFS CSI driver |
| `adot` | AWS Distro for OpenTelemetry |
| `amazon-cloudwatch-observability` | CloudWatch observability |
| `eks-pod-identity-agent` | EKS Pod Identity agent |

### Access Policy ARNs
| Policy | Description |
|--------|-------------|
| `arn:aws:eks::aws:cluster-access-policy/AmazonEKSClusterAdminPolicy` | Full cluster admin |
| `arn:aws:eks::aws:cluster-access-policy/AmazonEKSAdminPolicy` | Admin without RBAC management |
| `arn:aws:eks::aws:cluster-access-policy/AmazonEKSEditPolicy` | Edit most resources |
| `arn:aws:eks::aws:cluster-access-policy/AmazonEKSViewPolicy` | Read-only access |
| `arn:aws:eks::aws:cluster-access-policy/AmazonEKSAdminViewPolicy` | Admin read-only access |

### Wait Commands
| Waiter | Description |
|--------|-------------|
| `cluster-active` | Wait until cluster is active |
| `cluster-deleted` | Wait until cluster is deleted |
| `nodegroup-active` | Wait until node group is active |
| `nodegroup-deleted` | Wait until node group is deleted |
| `addon-active` | Wait until add-on is active |
| `addon-deleted` | Wait until add-on is deleted |
| `fargate-profile-active` | Wait until Fargate profile is active |
| `fargate-profile-deleted` | Wait until Fargate profile is deleted |
