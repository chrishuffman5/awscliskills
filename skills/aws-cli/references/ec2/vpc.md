# VPC

### 3.1 `aws ec2 create-vpc`

**Description:** Creates a VPC with specified CIDR blocks. A VPC must have an associated IPv4 CIDR block. By default, instances use Amazon-provided DHCP options.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--cidr-block` | string | Optional | IPv4 CIDR (e.g., `10.0.0.0/16`) |
| `--ipv4-ipam-pool-id` | string | Optional | IPv4 IPAM pool ID |
| `--ipv4-netmask-length` | integer | Optional | Netmask length from IPAM pool |
| `--amazon-provided-ipv6-cidr-block` | boolean | Optional | Request Amazon IPv6 /56 CIDR |
| `--ipv6-cidr-block` | string | Optional | IPv6 CIDR from your pool |
| `--ipv6-pool` | string | Optional | IPv6 address pool ID |
| `--ipv6-ipam-pool-id` | string | Optional | IPv6 IPAM pool ID |
| `--ipv6-netmask-length` | integer | Optional | IPv6 netmask length |
| `--ipv6-cidr-block-network-border-group` | string | Optional | Network border group for IPv6 |
| `--instance-tenancy` | string | Optional | `default`, `dedicated`, or `host` |
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "Vpc": {
    "VpcId": "string",
    "State": "pending|available",
    "CidrBlock": "string",
    "DhcpOptionsId": "string",
    "OwnerId": "string",
    "InstanceTenancy": "default|dedicated|host",
    "IsDefault": false,
    "CidrBlockAssociationSet": [
      {
        "AssociationId": "string",
        "CidrBlock": "string",
        "CidrBlockState": {
          "State": "associating|associated|disassociating|disassociated|failing|failed",
          "StatusMessage": "string"
        }
      }
    ],
    "Ipv6CidrBlockAssociationSet": [
      {
        "AssociationId": "string",
        "Ipv6CidrBlock": "string",
        "Ipv6CidrBlockState": { "State": "string", "StatusMessage": "string" },
        "Ipv6Pool": "string",
        "NetworkBorderGroup": "string"
      }
    ],
    "Tags": [{ "Key": "string", "Value": "string" }]
  }
}
```

---

### 3.2 `aws ec2 delete-vpc`

**Description:** Deletes a VPC. Must detach/delete all gateways, running instances, non-default security groups, and non-default route tables first.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--vpc-id` | string | **Required** | VPC ID to delete |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.3 `aws ec2 describe-vpcs`

**Description:** Describes your VPCs. Paginated operation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--vpc-ids` | list(string) | Optional | Specific VPC IDs |
| `--filters` | list(structure) | Optional | Filter criteria |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

**Filters:** `cidr`, `cidr-block-association.cidr-block`, `cidr-block-association.state`, `dhcp-options-id`, `is-default`, `owner-id`, `state` (`pending`/`available`), `tag:<key>`, `tag-key`, `vpc-id`

#### Output Schema

```json
{
  "NextToken": "string",
  "Vpcs": [
    {
      "VpcId": "string",
      "State": "pending|available",
      "CidrBlock": "string",
      "DhcpOptionsId": "string",
      "OwnerId": "string",
      "InstanceTenancy": "default|dedicated|host",
      "IsDefault": false,
      "CidrBlockAssociationSet": [
        {
          "AssociationId": "string",
          "CidrBlock": "string",
          "CidrBlockState": { "State": "string", "StatusMessage": "string" }
        }
      ],
      "Ipv6CidrBlockAssociationSet": [
        {
          "AssociationId": "string",
          "Ipv6CidrBlock": "string",
          "Ipv6CidrBlockState": { "State": "string" },
          "Ipv6Pool": "string",
          "NetworkBorderGroup": "string"
        }
      ],
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ]
}
```

---

### 3.4 `aws ec2 modify-vpc-attribute`

**Description:** Modifies a VPC attribute. DNS resolution and DNS hostnames cannot be modified in the same request. DNS hostnames requires DNS support to be enabled.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--vpc-id` | string | **Required** | VPC ID |
| `--enable-dns-hostnames` / `--no-enable-dns-hostnames` | boolean | Optional | DNS hostnames for instances |
| `--enable-dns-support` / `--no-enable-dns-support` | boolean | Optional | DNS resolution support |
| `--enable-network-address-usage-metrics` / `--no-enable-network-address-usage-metrics` | boolean | Optional | NAU metrics |

#### Output Schema

**None** -- no output on success.

---

### 3.5 `aws ec2 create-subnet`

**Description:** Creates a subnet in a VPC. Supports IPv4-only, IPv6-only, or dual-stack. IPv4 size: /28 to /16. AWS reserves first 4 and last 1 IP in each subnet.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--vpc-id` | string | **Required** | VPC ID |
| `--cidr-block` | string | Optional | IPv4 CIDR (e.g., `10.0.1.0/24`) |
| `--ipv6-cidr-block` | string | Optional | IPv6 CIDR |
| `--ipv6-native` / `--no-ipv6-native` | boolean | Optional | IPv6-only subnet |
| `--availability-zone` | string | Optional | AZ name (e.g., `us-east-1a`) |
| `--availability-zone-id` | string | Optional | AZ ID |
| `--outpost-arn` | string | Optional | Outpost ARN |
| `--ipv4-ipam-pool-id` | string | Optional | IPAM pool ID |
| `--ipv4-netmask-length` | integer | Optional | Netmask length |
| `--ipv6-ipam-pool-id` | string | Optional | IPv6 IPAM pool ID |
| `--ipv6-netmask-length` | integer | Optional | IPv6 netmask length |
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "Subnet": {
    "SubnetId": "string",
    "VpcId": "string",
    "State": "pending|available|unavailable|failed",
    "AvailabilityZone": "string",
    "AvailabilityZoneId": "string",
    "CidrBlock": "string",
    "AvailableIpAddressCount": 0,
    "DefaultForAz": false,
    "MapPublicIpOnLaunch": false,
    "Ipv6Native": false,
    "AssignIpv6AddressOnCreation": false,
    "OwnerId": "string",
    "SubnetArn": "string",
    "Ipv6CidrBlockAssociationSet": [
      {
        "AssociationId": "string",
        "Ipv6CidrBlock": "string",
        "Ipv6CidrBlockState": { "State": "string" }
      }
    ],
    "Tags": [{ "Key": "string", "Value": "string" }],
    "PrivateDnsNameOptionsOnLaunch": {
      "HostnameType": "ip-name|resource-name",
      "EnableResourceNameDnsARecord": false,
      "EnableResourceNameDnsAAAARecord": false
    }
  }
}
```

---

### 3.6 `aws ec2 delete-subnet`

**Description:** Deletes a subnet. All running instances must be terminated first.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--subnet-id` | string | **Required** | Subnet ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.7 `aws ec2 describe-subnets`

**Description:** Describes your subnets. Paginated operation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--subnet-ids` | list(string) | Optional | Specific subnet IDs |
| `--filters` | list(structure) | Optional | Filter criteria |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

**Filters:** `availability-zone`, `availability-zone-id`, `available-ip-address-count`, `cidr-block`, `default-for-az`, `ipv6-cidr-block-association.state`, `ipv6-native`, `map-public-ip-on-launch`, `owner-id`, `state`, `subnet-arn`, `subnet-id`, `tag:<key>`, `tag-key`, `vpc-id`

#### Output Schema

```json
{
  "NextToken": "string",
  "Subnets": [
    {
      "SubnetId": "string",
      "VpcId": "string",
      "State": "pending|available",
      "AvailabilityZone": "string",
      "AvailabilityZoneId": "string",
      "CidrBlock": "string",
      "AvailableIpAddressCount": 0,
      "DefaultForAz": false,
      "MapPublicIpOnLaunch": false,
      "OwnerId": "string",
      "SubnetArn": "string",
      "Ipv6Native": false,
      "AssignIpv6AddressOnCreation": false,
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ]
}
```

---

### 3.8 `aws ec2 create-internet-gateway`

**Description:** Creates an internet gateway for use with a VPC. After creation, attach it to a VPC using `attach-internet-gateway`.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "InternetGateway": {
    "Attachments": [{ "State": "attaching|attached|detaching|detached", "VpcId": "string" }],
    "InternetGatewayId": "string",
    "OwnerId": "string",
    "Tags": [{ "Key": "string", "Value": "string" }]
  }
}
```

---

### 3.9 `aws ec2 delete-internet-gateway`

**Description:** Deletes an internet gateway. Must detach from VPC first.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--internet-gateway-id` | string | **Required** | Internet gateway ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.10 `aws ec2 attach-internet-gateway`

**Description:** Attaches an internet gateway to a VPC, enabling internet connectivity.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--internet-gateway-id` | string | **Required** | Internet gateway ID |
| `--vpc-id` | string | **Required** | VPC ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.11 `aws ec2 detach-internet-gateway`

**Description:** Detaches an internet gateway from a VPC. The VPC must not contain running instances with Elastic IPs or public IPv4 addresses.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--internet-gateway-id` | string | **Required** | Internet gateway ID |
| `--vpc-id` | string | **Required** | VPC ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.12 `aws ec2 describe-internet-gateways`

**Description:** Describes your internet gateways. Paginated operation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--internet-gateway-ids` | list(string) | Optional | Specific gateway IDs |
| `--filters` | list(structure) | Optional | Filter criteria |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

**Filters:** `attachment.state`, `attachment.vpc-id`, `internet-gateway-id`, `owner-id`, `tag:<key>`, `tag-key`

#### Output Schema

```json
{
  "InternetGateways": [
    {
      "Attachments": [{ "State": "string", "VpcId": "string" }],
      "InternetGatewayId": "string",
      "OwnerId": "string",
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ],
  "NextToken": "string"
}
```

---

### 3.13 `aws ec2 create-route-table`

**Description:** Creates a route table for a VPC. After creation, add routes and associate with subnets.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--vpc-id` | string | **Required** | VPC ID |
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--client-token` | string | Optional | Idempotency token |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "RouteTable": {
    "RouteTableId": "string",
    "VpcId": "string",
    "OwnerId": "string",
    "Associations": [
      {
        "Main": false,
        "RouteTableAssociationId": "string",
        "RouteTableId": "string",
        "SubnetId": "string",
        "GatewayId": "string",
        "AssociationState": { "State": "string", "StatusMessage": "string" }
      }
    ],
    "Routes": [
      {
        "DestinationCidrBlock": "string",
        "DestinationIpv6CidrBlock": "string",
        "DestinationPrefixListId": "string",
        "GatewayId": "string",
        "InstanceId": "string",
        "NatGatewayId": "string",
        "TransitGatewayId": "string",
        "NetworkInterfaceId": "string",
        "VpcPeeringConnectionId": "string",
        "Origin": "CreateRouteTable|CreateRoute|EnableVgwRoutePropagation",
        "State": "active|blackhole"
      }
    ],
    "PropagatingVgws": [{ "GatewayId": "string" }],
    "Tags": [{ "Key": "string", "Value": "string" }]
  }
}
```

---

### 3.14 `aws ec2 delete-route-table`

**Description:** Deletes a route table. Must disassociate from all subnets first. Cannot delete the main route table.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--route-table-id` | string | **Required** | Route table ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.15 `aws ec2 describe-route-tables`

**Description:** Describes your route tables. Paginated operation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--route-table-ids` | list(string) | Optional | Specific route table IDs |
| `--filters` | list(structure) | Optional | Filter criteria |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

**Filters:** `association.gateway-id`, `association.route-table-association-id`, `association.route-table-id`, `association.subnet-id`, `association.main`, `owner-id`, `route-table-id`, `route.destination-cidr-block`, `route.destination-ipv6-cidr-block`, `route.gateway-id`, `route.instance-id`, `route.nat-gateway-id`, `route.transit-gateway-id`, `route.origin`, `route.state`, `tag:<key>`, `tag-key`, `vpc-id`

#### Output Schema

```json
{
  "RouteTables": [
    {
      "RouteTableId": "string",
      "VpcId": "string",
      "OwnerId": "string",
      "Associations": [
        {
          "Main": false,
          "RouteTableAssociationId": "string",
          "RouteTableId": "string",
          "SubnetId": "string",
          "GatewayId": "string",
          "AssociationState": { "State": "string", "StatusMessage": "string" }
        }
      ],
      "Routes": [
        {
          "DestinationCidrBlock": "string",
          "DestinationIpv6CidrBlock": "string",
          "GatewayId": "string",
          "NatGatewayId": "string",
          "TransitGatewayId": "string",
          "NetworkInterfaceId": "string",
          "InstanceId": "string",
          "VpcPeeringConnectionId": "string",
          "Origin": "string",
          "State": "active|blackhole"
        }
      ],
      "PropagatingVgws": [{ "GatewayId": "string" }],
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ],
  "NextToken": "string"
}
```

---

### 3.16 `aws ec2 create-route`

**Description:** Creates a route in a route table. Must specify a destination (CIDR or prefix list) and exactly one target.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--route-table-id` | string | **Required** | Route table ID |
| `--destination-cidr-block` | string | Optional* | IPv4 destination CIDR |
| `--destination-ipv6-cidr-block` | string | Optional* | IPv6 destination CIDR |
| `--destination-prefix-list-id` | string | Optional* | Prefix list destination |
| `--gateway-id` | string | Optional** | Internet/virtual private gateway |
| `--instance-id` | string | Optional** | NAT instance ID |
| `--nat-gateway-id` | string | Optional** | NAT gateway ID |
| `--network-interface-id` | string | Optional** | Network interface ID |
| `--vpc-peering-connection-id` | string | Optional** | VPC peering connection ID |
| `--egress-only-internet-gateway-id` | string | Optional** | Egress-only IGW (IPv6) |
| `--transit-gateway-id` | string | Optional** | Transit gateway ID |
| `--vpc-endpoint-id` | string | Optional** | Gateway Load Balancer endpoint |
| `--local-gateway-id` | string | Optional** | Local gateway ID |
| `--carrier-gateway-id` | string | Optional** | Carrier gateway (Wavelength) |
| `--core-network-arn` | string | Optional** | Core network ARN |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

*Specify exactly one destination. **Specify exactly one target.

#### Output Schema

```json
{
  "Return": true
}
```

---

### 3.17 `aws ec2 delete-route`

**Description:** Deletes a route from a route table. Destination must match exactly.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--route-table-id` | string | **Required** | Route table ID |
| `--destination-cidr-block` | string | Optional | IPv4 CIDR to match |
| `--destination-ipv6-cidr-block` | string | Optional | IPv6 CIDR to match |
| `--destination-prefix-list-id` | string | Optional | Prefix list ID to match |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.18 `aws ec2 associate-route-table`

**Description:** Associates a subnet or gateway with a route table. Returns an association ID needed for later disassociation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--route-table-id` | string | **Required** | Route table ID |
| `--subnet-id` | string | Optional | Subnet ID to associate |
| `--gateway-id` | string | Optional | Internet/virtual private gateway ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "AssociationId": "string",
  "AssociationState": {
    "State": "associating|associated|disassociating|disassociated|failed",
    "StatusMessage": "string"
  }
}
```

---

### 3.19 `aws ec2 disassociate-route-table`

**Description:** Disassociates a subnet or gateway from a route table. The subnet then uses the VPC's main route table.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--association-id` | string | **Required** | The association ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.20 `aws ec2 create-nat-gateway`

**Description:** Creates a NAT gateway in a subnet. **Public** NAT gateways route internet-bound traffic from private subnets. **Private** NAT gateways route to other VPCs/on-premises via transit gateway.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--subnet-id` | string | Optional | Subnet ID for the NAT gateway |
| `--vpc-id` | string | Optional | VPC ID (for regional NAT gateways) |
| `--allocation-id` | string | Optional | Elastic IP allocation ID (public NAT gateways only) |
| `--connectivity-type` | string | Optional | `public` (default) or `private` |
| `--availability-mode` | string | Optional | `zonal` (default) or `regional` |
| `--private-ip-address` | string | Optional | Private IPv4 address to assign |
| `--secondary-allocation-ids` | list(string) | Optional | Secondary EIP allocation IDs |
| `--secondary-private-ip-addresses` | list(string) | Optional | Secondary private IPs |
| `--secondary-private-ip-address-count` | integer | Optional | Number of secondary private IPs (1-31) |
| `--client-token` | string | Optional | Idempotency token |
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "ClientToken": "string",
  "NatGateway": {
    "CreateTime": "timestamp",
    "NatGatewayAddresses": [
      {
        "AllocationId": "string",
        "NetworkInterfaceId": "string",
        "PrivateIp": "string",
        "PublicIp": "string",
        "AssociationId": "string",
        "IsPrimary": true,
        "Status": "assigning|associating|succeeded|failed"
      }
    ],
    "NatGatewayId": "string",
    "State": "pending|failed|available|deleting|deleted",
    "SubnetId": "string",
    "VpcId": "string",
    "ConnectivityType": "private|public",
    "Tags": [{ "Key": "string", "Value": "string" }]
  }
}
```

---

### 3.21 `aws ec2 delete-nat-gateway`

**Description:** Deletes a NAT gateway. Disassociates but does not release the Elastic IP. Does not delete NAT gateway routes in route tables.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--nat-gateway-id` | string | **Required** | NAT gateway ID |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "NatGatewayId": "string"
}
```

---

### 3.22 `aws ec2 describe-nat-gateways`

**Description:** Describes your NAT gateways. Paginated operation.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--nat-gateway-ids` | list(string) | Optional | Specific NAT gateway IDs |
| `--filter` | list(structure) | Optional | Filters: `nat-gateway-id`, `state`, `subnet-id`, `tag`, `tag-key`, `vpc-id` |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

#### Output Schema

```json
{
  "NatGateways": [
    {
      "CreateTime": "timestamp",
      "DeleteTime": "timestamp",
      "FailureCode": "string",
      "FailureMessage": "string",
      "NatGatewayAddresses": [
        {
          "AllocationId": "string",
          "NetworkInterfaceId": "string",
          "PrivateIp": "string",
          "PublicIp": "string",
          "IsPrimary": true,
          "Status": "string"
        }
      ],
      "NatGatewayId": "string",
      "State": "pending|failed|available|deleting|deleted",
      "SubnetId": "string",
      "VpcId": "string",
      "ConnectivityType": "public|private",
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ],
  "NextToken": "string"
}
```

---

### 3.23 `aws ec2 allocate-address`

**Description:** Allocates an Elastic IP address to your AWS account. Supports Amazon's pool, BYOIP pools, IPAM pools, CoIP pools (Outposts), and Carrier IPs (Wavelength).

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--domain` | string | Optional | `vpc` or `standard` |
| `--address` | string | Optional | Specific IP to recover or allocate |
| `--public-ipv4-pool` | string | Optional | Your address pool ID |
| `--network-border-group` | string | Optional | AZ/Local Zone/Wavelength Zone group |
| `--customer-owned-ipv4-pool` | string | Optional | CoIP pool ID (Outposts) |
| `--ipam-pool-id` | string | Optional | IPAM pool ID |
| `--tag-specifications` | list(structure) | Optional | Tags on creation |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "AllocationId": "string",
  "PublicIp": "string",
  "PublicIpv4Pool": "string",
  "NetworkBorderGroup": "string",
  "Domain": "vpc|standard",
  "CustomerOwnedIp": "string",
  "CustomerOwnedIpv4Pool": "string",
  "CarrierIp": "string"
}
```

---

### 3.24 `aws ec2 release-address`

**Description:** Releases an Elastic IP address back to the pool. For default VPCs, automatically disassociates. For non-default VPCs, must disassociate first.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--allocation-id` | string | Optional | Allocation ID (VPC) |
| `--public-ip` | string | Optional | Public IP (EC2-Classic, deprecated) |
| `--network-border-group` | string | Optional | Network border group |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

**None** -- no output on success.

---

### 3.25 `aws ec2 describe-addresses`

**Description:** Describes specified or all Elastic IP addresses.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--public-ips` | list(string) | Optional | Specific Elastic IPs |
| `--allocation-ids` | list(string) | Optional | Specific allocation IDs |
| `--filters` | list(structure) | Optional | Filters: `allocation-id`, `association-id`, `instance-id`, `domain`, `network-interface-id`, `private-ip-address`, `public-ip`, `tag:<key>`, `tag-key` |
| `--dry-run` / `--no-dry-run` | boolean | Optional | Permission check |

#### Output Schema

```json
{
  "Addresses": [
    {
      "AllocationId": "string",
      "AssociationId": "string",
      "Domain": "vpc|standard",
      "NetworkInterfaceId": "string",
      "NetworkInterfaceOwnerId": "string",
      "PrivateIpAddress": "string",
      "PublicIp": "string",
      "PublicIpv4Pool": "string",
      "NetworkBorderGroup": "string",
      "InstanceId": "string",
      "SubnetId": "string",
      "Tags": [{ "Key": "string", "Value": "string" }]
    }
  ]
}
```

---

