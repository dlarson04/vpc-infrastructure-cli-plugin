---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-05-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# IBM Cloud CLI for VPC Reference
{: #vpc-reference}

This document provides a reference of the command line interface (CLI) commands available for the functionality of the {{site.data.keyword.cloud}} Virtual Private Cloud. The commands are organized into sections according to functionality: first for setting the target version of Virtual Private Cloud you'll be using, then for network, compute, regions, VPN, load balancers, and storage. Similar commands to execute these functions also are available as [API commands](https://{DomainName}/apidocs/vpc-on-classic){:new_window}.

## Prerequisites:

Install the [IBM Cloud CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#overview){: new_window}.

Install or update the vpc-infrastructure plugin.

  ```
  ibmcloud plugin install vpc-infrastructure
  ```
  {: pre}

  To update:

  ```
  ibmcloud plugin update
  ```
  {: pre}

  To view installed plugins and versions:

  ```
  ibmcloud plugin list
  ```
  {: pre}



## Target Commands
{: #target}

This command targets the generation of Virtual Private Cloud, 1 (on Classic), or 2 (Next Generation). 

### `ibmcloud is target`

`ibmcloud is target [--gen 2 | 1]`

**Options**

- `--gen`: Generation of Virtual Private Cloud. Default is 2.


## Network Commands
{: #network}

This section provides a reference to the command line interface (CLI) commands available for the network functionality and resources, including floating IPs, public gateways, network ACLs, subnets, security groups, and VPCs.

## Floating IPs

### `ibmcloud is floating-ips`
{: #floating-ips-cli}

**List all floating IPs.**

`ibmcloud is floating-ips [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is floating-ip`
{: #floating-ip}

**View details of a floating IP.**

`ibmcloud is floating-ip FLOATING_IP_ID [--json]`

**Options**

- `FLOATING_IP_ID`: ID of the floating IP.
- `--json`: Format output in JSON.

---

### `ibmcloud is floating-ip-reserve`
{: #floating-ip-reserve}

**Reserve a floating IP.**

`ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE | --nic-id NIC_ID) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**

- `FLOATING_IP_NAME`: Name of the floating IP.
- `--zone`: Name of the target zone. This option is exclusive with `--nic-id`.
- `--nic-id`: ID of the target network interface. This option is exclusive with `--zone`.
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is floating-ip-release`
{: #floating-ip-release}

**Release a floating IP.**

`ibmcloud is floating-ip-release FLOATING_IP_ID [-f, --force]`

**Options**

- `FLOATING_IP_ID`: ID of the floating IP.
- `--force, -f`: Release without confirmation.

---

### `ibmcloud is floating-ip-update`
{: #floating-ip-update}

**Update a floating IP.**

`ibmcloud is floating-ip-update FLOATING_IP_ID [--name NEW_NAME] [--nic-id NIC_ID] [--json]`

**Options**

- `FLOATING_IP_ID`: ID of the floating IP.
- `--name`: New name of the floating IP.
- `--nic-id`: ID of the network interface to associate.
- `--json`: Format output in JSON.



## Public Gateways

### `ibmcloud is public-gateways`
{: #public-gateways-cli}

**List all public gateways.**

`ibmcloud is public-gateways [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is public-gateway`
{: #public-gateway}

**View details of a public gateway.**

`ibmcloud is public-gateway GATEWAY_ID [--json]`

**Options**

- `GATEWAY_ID`: ID of the public gateway.
- `--json`: Format output in JSON.

---

### `ibmcloud is public-gateway-create`
{: #public-gateway-create}

**Create a public gateway.**

`ibmcloud is public-gateway-create GATEWAY_NAME VPC_ID ZONE  [--floating-ip-id IP_ID | --floating-ip-address IP_ADDRESS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**

- `GATEWAY_NAME`: Name of the public gateway.
- `VPC_ID`: ID of the VPC.
- `ZONE`: Name of the zone.
- `--floating-ip-id`: ID of the floating IP bound to the public gateway.
- `--floating-ip-address`: IP address of the floating IP bound to the public gateway.
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is public-gateway-update`
{: #public-gateway-update}

**Update a public gateway.**

`ibmcloud is public-gateway-update GATEWAY_ID --name NEW_NAME [--json]`

**Options**

- `GATEWAY_ID`: ID of the public gateway.
- `--name`: New name of the public gateway.
- `--json`: Format output in JSON.

---

### `ibmcloud is public-gateway-delete`
{: #public-gateway-delete}

**Delete a public gateway.**

`ibmcloud is public-gateway-delete GATEWAY_ID [-f, --force]`

**Options**

- `GATEWAY_ID`: ID of the public gateway.
- `--force, -f`: Delete without confirmation.



## Network ACLs

### `ibmcloud is network-acls`
{: #network-acls-cli}

**List all network ACLs.**

`ibmcloud is network-acls [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl`
{: #network-acl}

**View details of a network ACL.**

`ibmcloud is network-acl ACL_ID [--json]`

**Options**

- `ACL_ID`: ID of the network ACL.
- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl-create`
{: #network-acl-create}

**Create a network ACL.**

`ibmcloud is network-acl-create ACL_NAME [--source-acl-id SOURCE_ACL_ID] [--json]`

**Options**

- `ACL_NAME`: Name of the network acl.
- `--source-acl-id`: ID of the network ACL contains rules to be copied.
- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl-update`
{: #network-acl-update}

**Update a network ACL.**

`ibmcloud is network-acl-update ACL_ID --name NEW_NAME [--json]`

**Options**

- `ACL_ID`: ID of the network ACL.
- `--name`: New name of the network ACL.
- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl-delete`
{: #network-acl-delete}

**Delete a network ACL.**

`ibmcloud is network-acl-delete ACL_ID [-f, --force]`

**Options**

- `ACL_ID`: ID of the network ACL
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is network-acl-rules`
{: #network-acl-rules}

**List all rules of a network ACL.**

`ibmcloud is network-acl-rules ACL_ID [--json]`

**Options**

- `ACL_ID`: ID of the network ACL.
- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl-rule`
{: #network-acl-rule}

**View details of a network ACL rule.**

`ibmcloud is network-acl-rule ACL_ID RULE_ID [--json]`

**Options**

- `ACL_ID`: ID of the network ACL.
- `RULE_ID`: ID of the rule.
- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl-rule-add`
{: #network-acl-rule-add}

**Add a rule to a network ACL.**

`ibmcloud is network-acl-rule-add RULE_NAME ACL_ID ACTION DIRECTION PROTOCOL SOURCE DESTINATION  [--icmp-code ICMP_CODE] [--icmp-type ICMP_TYPE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-max PORT_MAX] [---destination-port-min PORT_MIN] [--before-rule-id RULE_ID] [--json]`


**Options**

- `RULE_NAME`: Name of the rule.
- `ACL_ID`: ID of the network ACL.
- `ACTION`: Enumeration type: `allow` or `deny`.
- `DIRECTION`: Direction of traffic to enforce. Enumeration type: `inbound` or `outbound`.
- `SOURCE`: Source IP address or CIDR block.
- `DESTINATION`: Destination IP address or CIDR block.
- `PROTOCOL`: Protocol to enforce. Enumeration type: `all`, `icmp`, `tcp` or `udp`.
- `--icmp-type`: ICMP traffic type to allow. Valid values from 0 to 254. This option is specified only when protocol is set to `icmp`. If unspecified, all types are allowed.
- `--icmp-code`: ICMP traffic code to allow. Valid values from 0 to 255. This option is specified only when protocol is set to `icmp`. If unspecified, all codes are allowed.
- `--destination-port-min`: Minimum destination port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp` (default: 1).
- `--destination-port-max`: Maximum destination port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp` (default: 65535).
- `--source-port-min`: Minimum source port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp` (default: 1).
- `--source-port-max`: Maximum source port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp` (default: 65535).
- `--before-rule-id`: ID of the rule that this rule is inserted before.
- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl-rule-update`
{: #network-acl-rule-update}

**Update a rule of a network ACL.**
`ibmcloud is network-acl-rule-update ACL_ID RULE_ID [--action ACTION] [--direction DIRECTION] [--source SOURCE] [--dest DEST] [--protocol PROTOCOL] [--icmp-code ICMP_CODE] [--icmp-type ICMP_TYPE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-max PORT_MAX] [---destination-port-min PORT_MIN] [--before-rule-id RULE_ID] [--json]`

**Options**

- `ACL_ID`: ID of the network ACL.
- `RULE_ID`: ID of the rule.
- `--name`: New name of the rule.
- `--direction`: Direction of traffic to enforce. Enumeration type: `inbound` or `outbound`.
- `--action`: Enumeration type: `allow` or `deny`.
- `--protocol`: Protocol to enforce. Enumeration type: `all`, `icmp`, `tcp` or `udp`.
- `--before-rule-id`: ID of the rule that this rule is inserted before.
- `--source`: Source IP address or CIDR block.
- `--dest`: Destination IP address or CIDR block.
- `--icmp-type`: ICMP traffic type to allow. Valid values from 0 to 254. This option is specified only when protocol is set to `icmp`.
- `--icmp-code`: ICMP traffic code to allow. Valid values from 0 to 255. This option is specified only when protocol is set to `icmp`.
- `--destination-port-min`: Minimum destination port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp`.
- `--destination-port-max`: Maximum destination port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp`.
- `--source-port-min`: Minimum source port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp`.
- `--source-port-max`: Maximum source port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp`.
- `--json`: Format output in JSON.

---

### `ibmcloud is network-acl-rule-delete`
{: #network-acl-rule-delete}

**Delete a rule from a network ACL.**

`ibmcloud is network-acl-rule-delete ACL_ID RULE_ID [-f, --force]`

**Options**

- `ACL_ID`: ID of the network ACL.
- `RULE_ID`: ID of the rule.
- `--force, -f`: Delete without confirmation.

---

## Subnets

### `ibmcloud is subnets`
{: #subnets-cli}

**List all subnets.**

`ibmcloud is subnets [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is subnet`
{: #subnet}

**View details of a subnet.**

`ibmcloud is subnet SUBNET_ID [--json]`

**Options**

- `SUBNET_ID`: ID of the subnet.
- `--json`: Format output in JSON.

---

### `ibmcloud is subnet-create`
{: #subnet-create}

**Create a subnet.**

`ibmcloud is subnet-create SUBNET_NAME VPC_ID ZONE (--ipv4-cidr-block CIDR_BLOCK | --ipv4-address-count ADDR_COUNT) [--network-acl-id NETWORK_ACL_ID] [--public-gateway-id PUBLIC_GATEWAY] [--json]`

**Options**

- `SUBNET_NAME`: Name of the subnet.
- `VPC_ID`: ID of the VPC.
- `ZONE`: Name of the zone.
- `--network-acl-id`: The ID of the network ACL.
- `--public-gateway-id`: The ID of the public gateway.
- `--ipv4-cidr-block`: The IPv4 range of the subnet, this is exclusive with `--ipv4-address-count`.
- `--ipv4-address-count`: The total number of IPv4 addresses required. This option is exclusive with `--ipv4-cidr-block`.
- `--json`: Format output in JSON.

---

### `ibmcloud is subnet-update`
{: #subnet-update}

**Update a subnet.**

`ibmcloud is subnet-update SUBNET_ID [--name NEW_NAME] [--network-acl-id NETWORK_ACL_ID] [--public-gateway-id PUBLIC_GATEWAY_ID] [--json]`

**Options**

- `SUBNET_ID`: ID of the subnet.
- `--name`: New name of the subnet.
- `--network-acl-id`: ID of the network ACL.
- `--public-gateway-id`: ID of the public gateway.
- `--json`: Format output in JSON.

---

### `ibmcloud is subnet-delete`
{: #subnet-delete}

**Delete a subnet.**

`ibmcloud is subnet-delete SUBNET_ID [-f, --force]`

**Options**

- `SUBNET_ID`: ID of the subnet.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is subnet-public-gateway-detach`
{: #subnet-public-gateway-detach}

**Detach the public gateway from a subnet.**

`ibmcloud is subnet-public-gateway-detach SUBNET_ID [-f, --force]`

**Options**

- `SUBNET_ID`: ID of the subnet.
- `--force, -f`: Detach without confirmation.

---

### `ibmcloud is subnet-public-gateway`

**View details of public gateway attached to the subnet.**

`ibmcloud is subnet-public-gateway SUBNET_ID [--json]`

**options**

- `SUBNET_ID`: ID of the subnet.
- `--json`: Format output in JSON.

---

### `ibmcloud is subnet-network-acl-detach`
{: #subnet-network-acl-detach}

**Detach the network ACL from a subnet.**

`ibmcloud is subnet-network-acl-detach SUBNET_ID [-f, --force]`

**Options**

- `SUBNET_ID`: ID of the subnet.
- `--force, -f`: Detach without confirmation.



## Security Groups

### `ibmcloud is security-groups`
{: #security-groups-cli}


**List all security groups.**

`ibmcloud is security-groups [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is security-group`
{: #security-group}

**View details of a security group.**

`ibmcloud is security-group GROUP_ID [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-create`
{: #security-group-create}

**Create a security group.**

`ibmcloud is security-group-create GROUP_NAME VPC_ID [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**

- `GROUP_NAME`: Name of the subnet.
- `VPC_ID`: ID of the VPC.
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-update`
{: #security-group-update}

**Update a security group.**

`ibmcloud is security-group-update GROUP_ID [--name NEW_NAME] [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `--name`: New name of the security group.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-delete`
{: #security-group-delete}

**Delete a security group.**

`ibmcloud is security-group-delete GROUP_ID [-f, --force]`

**Options**

- `GROUP_ID`: ID of the security group.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is security-group-network-interfaces`
{: #security-group-network-interfaces}

**List all network interfaces of a security group.**

`ibmcloud is security-group-network-interfaces GROUP_ID [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-network-interface`
{: #security-group-network-interface}

**View details of a network interface of a security group.**

`ibmcloud is security-group-network-interface GROUP_ID NIC_ID [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `NIC_ID`: ID of the network interface.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-network-interface-add`
{: #security-group-network-interface-add}

**Add a network interface to a security group.**

`ibmcloud is security-group-network-interface-add GROUP_ID NIC_ID [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `NIC_ID`: ID of the network interface.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-network-interface-remove`
{: #security-group-network-interface-remove}

**Remove a network interface from a security group.**

`ibmcloud is security-group-network-interface-remove GROUP_ID NIC_ID [-f, --force]`

**Options**

- `GROUP_ID`: ID of the security group.
- `NIC_ID`: ID of the network interface.
- `--force, -f`: Remove without confirmation.

---

### `ibmcloud is security-group-rules`
{: #security-group-rules}

**List all rules of a security group.**

`ibmcloud is security-group-rules GROUP_ID [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-rule`
{: #security-group-rule}

**View details of a security group rule.**

`ibmcloud is security-group-rule GROUP_ID RULE_ID [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `RULE_ID`: ID of the rule.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-rule-add`
{: #security-group-rule-add}

**Add a rule to a security group.**

`ibmcloud is security-group-rule-add GROUP_ID DIRECTION PROTOCOL [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP_ID] [--icmp-code ICMP_CODE] [--icmp-type ICMP_TYPE] [--port-max PORT_MAX] [--port-min PORT_MIN] [--json]`

**Options**

- `GROUP_ID`: ID of the security group.
- `DIRECTION`: Direction of traffic to enforce. Enumeration type: `inbound` or `outbound`.
- `PROTOCOL`: Protocol to enforce. Enumeration type: `all`, `icmp`, `tcp` or `udp`.
- `--remote`: The set of network interfaces from which this rule allows traffic, Can be specified as either an REMOTE_ADDRESS, CIDR_BLOCK or SECURITY_GROUP_ID.
- `--icmp-type`: ICMP traffic type to allow. Valid values from 0 to 254. This option is specified only when protocol is set to `icmp`. If unspecified, all types are allowed.
- `--icmp-code`: ICMP traffic code to allow. Valid values from 0 to 255. This option is specified only when protocol is set to `icmp`. If unspecified, all codes are allowed.
- `--port-min`: Minimum port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp` (default: 1).
- `--port-max`: Maximum port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp` (default: 65535).
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-rule-update`
{: #security-group-rule-update}

**Update a rule of a security group.**

`ibmcloud is security-group-rule-update GROUP_ID RULE_ID [--direction DIRECTION] [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP_ID] [--icmp-code ICMP_CODE] [--icmp-type ICMP_TYPE] [--port-max PORT_MAX] [--port-min PORT_MIN] [--json]`

**Options**

- `GROUP_NAME`: Name of the security group.
- `GROUP_ID`: ID of the security group.
- `RULE_ID`: ID of the rule.
- `--direction`: Direction of traffic to enforce. Enumeration type: `inbound` or `outbound`.
- `--remote`: The set of network interfaces from which this rule allows traffic, Can be specified as either an REMOTE_ADDRESS, CIDR_BLOCK or SECURITY_GROUP_ID.
- `--icmp-type`: ICMP traffic type to allow. Valid values from 0 to 254. This option is specified only when protocol is set to `icmp`.
- `--icmp-code`: ICMP traffic code to allow. Valid values from 0 to 255. This option is specified only when protocol is set to `icmp`.
- `--port-min`: Minimum port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp`.
- `--port-max`: Maximum port number. Valid values are from 1 to 65535. This option is specified only when protocol is set to `tcp` or `udp`.
- `--json`: Format output in JSON.

---

### `ibmcloud is security-group-rule-delete`
{: #security-group-rule-delete}

**Delete a rule from a security group.**

`ibmcloud is security-group-rule-delete GROUP_ID RULE_ID [-f, --force]`

**Options**

- `GROUP_ID`: ID of the security group.
- `RULE_ID`: ID of the rule.
- `--force, -f`: Delete without confirmation.



## VPCs

### `ibmcloud is vpcs`
{: #vpcs-cli}

**List all VPCs.**

`ibmcloud is vpcs [--classic-access] [--json]`

**Options**

- `--classic-access`: This flag lists VPCs that have Classic access enabled. The default value is false.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc`
{: #vpc}

**View details of a VPC.**

`ibmcloud is vpc VPC_ID [--json]`

**Options**

- `VPC_ID`: ID of the VPC
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc-create`
{: #vpc-create}

**Create a VPC.**

`ibmcloud is vpc-create VPC_NAME [--classic-access] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**

- `VPC_NAME`: Name of the VPC
- `--classic-access`: This flag indicates whether the VPC should be connected to Classic Infrastructure. The default  is false.
- `--resource-group-id`: ID of the resource group. This option is mutually exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is mutually exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc-update`
{: #vpc-update}

**Update a VPC.**

`ibmcloud is vpc-update VPC_ID [--name NEW_NAME] [--json]`

**Options**

- `VPC_ID`: ID of the VPC.
- `--name`: New name of the VPC.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc-delete`
{: #vpc-delete}

**Delete a VPC.**

`ibmcloud is vpc-delete VPC_ID [-f, --force]`

**Options**

- `VPC_ID`: ID of the VPC.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is vpc-default-security-group`
{: #vpc-default-security-group}

**View details of the default security group of a VPC.**

`ibmcloud is vpc-default-security-group VPC_ID [--json]`

**Options**

- `VPC_ID`: ID of the VPC.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc-address-prefix`
{: #vpc-address-prefix}

**View details of a VPC address prefix.**

`ibmcloud is vpc-address-prefix VPC_ID PREFIX_ID [--json]`

**Options**

- `VPC_ID`: ID of the VPC.
- `PREFIX_ID`: ID of the address prefix.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc-address-prefix-create`
{: #vpc-address-prefix-create}

**Create an address prefix.**

`ibmcloud is vpc-address-prefix-create PREFIX_NAME VPC_ID ZONE CIDR [--json]`

**Options**

- `PREFIX_NAME`: Name of the address prefix.
- `VPC_ID`: ID of the VPC.
- `ZONE`: Name of the zone.
- `CIDR`: The CIDR block for this prefix.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc-address-prefix-delete`
{: #vpc-address-prefix-delete}

**Delete an address prefix.**

`ibmcloud is vpc-address-prefix-delete VPC_ID PREFIX_ID [--force]`

**Options**

- `VPC_ID`: ID of the VPC.
- `PREFIX_ID`: ID of the address prefix.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is vpc-address-prefix-update`
{: #vpc-address-prefix-update}

**Update an address prefix.**

`ibmcloud is vpc-address-prefix-update VPC_ID PREFIX_ID [--name NEW_NAME] [--cidr CIDR] [--json]`

**Options**

- `VPC_ID`: ID of the VPC.
- `PREFIX_ID`: ID of the address prefix.
- `--name`: New name of the address prefix.
- `--cidr`: New CIDR block for the address prefix.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpc-address-prefixes`
{: #vpc-address-prefixes}

**List all address prefixes.**

`ibmcloud is vpc-address-prefixes VPC_ID [--json]`

**Options**

- `VPC_ID`: ID of the VPC.
- `--json`: Format output in JSON.



## Compute CLI commands
{: #compute}

This section contains a reference for the CLI commands related to Compute functionality in the IBM Cloud VPC, including profiles, images, keys, and instances. Similar commands to execute these functions also are available as [API commands](/docs/vpc-on-classic?topic=vpc-on-classic-api-reference-for-vpc-on-classic).


## Profiles

### `ibmcloud is instance-profiles`
{: #instance-profiles}

**List all server instance profiles in the region.**

`ibmcloud is instance-profiles [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is instance-profile`
{: #instance-profile}

**View details of a server instance profile.**

`ibmcloud is instance-profile PROFILE_NAME [--json]`

**Options**

- `PROFILE_NAME`: Name of the profile.
- `--json`: Format output in JSON.



## Images

### `ibmcloud is images`
{: #images-cli}

**List all images in the region.**

`ibmcloud is images [--visibility VISIBILITY] [--json]`

**Options**

- `--visibility`: List images with given visibility. Valid visibility is: public, private.
- `--json`: Format output in JSON.

---

### `ibmcloud is image`
{: #image}

**View details of an image.**

`ibmcloud is image IMAGE_ID [--json]`

**Options**

- `IMAGE_ID`: ID of the image.
- `--json`: Format output in JSON.



## Keys

### `ibmcloud is keys`
{: #keys-cli}

**List all keys.**

`ibmcloud is keys [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is key`
{: #key}

**View details of a key.**

`ibmcloud is key KEY_ID [--json]`

**Options**

- `KEY_ID`: ID of the key.
- `--json`: Format output in JSON.

---

### `ibmcloud is key-create`
{: #key-create}

**Import an RSA public key.**

`ibmcloud is key-create KEY_NAME (KEY | @KEY_FILE) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**

- `KEY_NAME`: Name of the key.
- `KEY`: key|@key-file. The public SSH key to be imported into the system.
- `--resource-group-id`: ID of the resource group. This option is mutually exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is mutually exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is key-update`
{: #key-update}

**Update the name of a key.**

`ibmcloud is key-update KEY_ID --name NEW_NAME [--json]`

**Options**

- `KEY_ID`: ID of the key.
- `--name`: New name for the key.
- `--json`: Format output in JSON.

---

### `ibmcloud is key-delete`
{: #key-delete}

**Delete a key.**

`ibmcloud is key-delete KEY_ID [-f, --force]`

**Options**

- `KEY_ID`: ID of the key.
- `--force, -f`: Delete without confirmation.



## Instances

### `ibmcloud is instances`
{: #instances-cli}

**List all server instances.**

`ibmcloud is instances [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is instance`
{: #instance}

**View details of a server instance.

`ibmcloud is instance INSTANCE_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server intance.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-create`
{: #instance-create}

**Create a server instance.**

`ibmcloud is instance-create INSTANCE_NAME VPC_ID ZONE_NAME PROFILE_NAME SUBNET_ID (--image-id IMAGE_ID) [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] (--key-ids IDS) [--user-data DATA] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--security-group-ids SECURITY_GROUP_IDS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`


**Options**

- `INSTANCE_NAME`: Name of the server instance.
- `VPC_ID`: ID of the VPC.
- `ZONE_NAME`: Name of the zone.
- `PROFILE_NAME`: Name of the profile.
- `SUBNET_ID`: The network interface associated subnet ID.
- `--boot-volume`: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in json or json file.
- `--volume-attach`: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in json or json file.
- `--image-id`: ID of the image.
- `--security-group-ids`: Comma-separated security group IDs for primary network interface.
- `--key-ids`: Comma-separated IDs of SSH keys.
- `--user-data`: data|@data-file. The user data to transfer to the server instance.
- `--network-interface`: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or as a JSON file.
- `--resource-group-id`: ID of the resource group. This option is mutually exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is mutually exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-update`
{: #instance-update}


**Update a server instance.

`ibmcloud is instance-update INSTANCE_ID [--name NEW_NAME] [--profile PROFILE_NAME] [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `--name`: New name of the server instance.
- `--profile`: Name of the profile.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-delete`
{: #instance-delete}

**Delete a server instance.**

`ibmcloud is instance-delete INSTANCE_ID [-f, --force]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is instance-initialization-values`
{: #instance-initialization-values}

**View initialization details of a server instance.**

`ibmcloud is instance-initialization-values INSTANCE_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-start`
{: #instance-start}

**Start a server instance.**

`ibmcloud is instance-start INSTANCE_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-stop`
{: #instance-stop}

**Stop a server instance.**

`ibmcloud is instance-stop INSTANCE_ID [-f, --force] [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `--json`: Format output in JSON.
- `--force, -f`: Stop without confirmation.

---

### `ibmcloud is instance-reboot`
{: #instance-reboot}

**Reboot a server instance.**

`ibmcloud is instance-reboot INSTANCE_ID [-f, --force] [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `--json`: Format output in JSON.
- `--force, -f`: Reboot without confirmation.

---

### `ibmcloud is instance-reset`
{: #instance-reset}

**Reset a server instance.**

`ibmcloud is instance-reset INSTANCE_ID [-f, --force] [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `--json`: Format output in JSON.
- `--force, -f`: Reset without confirmation.

---

### `ibmcloud is instance-network-interfaces`
{: #instance-network-interfaces}

**List all network interfaces of a server instance.**

`ibmcloud is instance-network-interfaces INSTANCE_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-network-interface`
{: #instance-network-interface}

**View details of a network interface of a server instance.**

`ibmcloud is instance-network-interface INSTANCE_ID NIC_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `NIC_ID`: ID of the network interface.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-network-interface-floating-ips`
{: #instance-network-interface-floating-ips}

**List all floating IPs associated with a network interface.**

`ibmcloud is instance-network-interface-floating-ips INSTANCE_ID NIC_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `NIC_ID`: ID of the NIC.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-network-interface-floating-ip`
{: #instance-network-interface-floating-ip}

**View details of a floating IP associated with a network interface.**

`ibmcloud is instance-network-interface-floating-ip INSTANCE_ID NIC_ID FLOATING_IP_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `NIC_ID`: ID of the NIC.
- `FLOATING_IP_ID`: ID of the floating IP.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-network-interface-floating-ip-add`
{: #instance-network-interface-floating-ip-add}

**Associate a floating IP with a network interface.**

`ibmcloud is instance-network-interface-floating-ip-add INSTANCE_ID NIC_ID FLOATING_IP_ID [--json]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `NIC_ID`: ID of the NIC.
- `FLOATING_IP_ID`: ID of the floating IP.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-network-interface-floating-ip-remove`
{: #instance-network-interface-floating-ip-remove}

**Disassociate a floating IP from a network interface.**

`ibmcloud is instance-network-interface-floating-ip-remove INSTANCE_ID NIC_ID FLOATING_IP_ID [-f, --force]`

**Options**

- `INSTANCE_ID`: ID of the server instance.
- `NIC_ID`: ID of the NIC.
- `FLOATING_IP_ID`: ID of the floating IP.
- `--force, -f`: Remove without confirmation.

---

### `ibmcloud is instance-volume-attachment`

**View details of a volume attachment of a server instance.**

`ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]`

**options**

- `INSTANCE_ID`: ID of the server instance.
- `VOLUME_ATTACHMENT_ID`: ID of the volume attachment.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-volume-attachment-add`

**Create a volume attachment for a server instance in the current resource group.

`ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]`

**options**

- `NAME`: Name of the volume attachment.
- `INSTANCE_ID`: ID of the server instance.
- `VOLUME_ID`: ID of the volume.
- `--auto-delete`: The attached volume will be deleted when deleting the instance, default is false.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-volume-attachment-detach`

**Delete a volume attachment from a server instance.**

`ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]`

**options**

- `INSTANCE_ID`: ID of the server instance.
- `VOLUME_ATTACHMENT_ID`: ID of the volume attachment.
- `--force, -f`: Force the operation without confirmation.

---

### `ibmcloud is instance-volume-attachment-update`

**Update a volume attachment.**

`ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]`

**options**

- `INSTANCE_ID`: ID of the server instance.
- `VOLUME_ATTACHMENT_ID`: ID of the volume attachment.
- `--name`: New name of the volume.
- `--auto-delete`: The attached volume will be deleted when deleting the instance, default is false.
- `--json`: Format output in JSON.

---

### `ibmcloud is instance-volume-attachments`

**List all volume attachments of a server instance.**

`ibmcloud is instance-volume-attachments INSTANCE_ID [--json]`

**options**

- `INSTANCE_ID`: ID of the server instance.
- `--json`: Format output in JSON.



## Regions and Zones CLI commands
{: #geography}

This section gives details about the CLI commands available for working with regions and zones.



## VPC Regions Commands

This section contains commands related to the functionality of geograpical regions and zones.

### `ibmcloud is regions`
{: #regions-cli}

**List all regions.**

`ibmcloud is regions [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is region`
{: #region}

**View details of a region.**

`ibmcloud is region REGION_NAME [--json]`

**Options**

- `REGION_NAME`: Name of region.
- `--json`: Format output in JSON.



## Zones

### `ibmcloud is zones`
{: #zones}

**List all zones in the target region.**

`ibmcloud is zones [--json]`

**Options**

- `REGION_NAME`: Name of region.
- `--json`: Format output in JSON.

---

### `ibmcloud is zone`

**View details of a zone in the target region.**

`ibmcloud is zone ZONE_NAME [--json]`

**Options**

- `REGION_NAME`: Name of region.
- `ZONE_NAME`: Name of zone.
- `--json`: Format output in JSON.


## VPN Commands
{: #vpn}

This section gives details about the CLI commands available for working with VPN, including IKE and IPsec policies.

## IKE Policies

### `ibmcloud is ike-policies`
{: #ike-policies}

**List all IKE policies.**

`ibmcloud is ike-policies [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is ike-policy`
{: #ike-policy}

**View details of an IKE policy.**

`ibmcloud is ike-policy IKE_POLICY_ID [--json]`

**Options**

- `IKE_POLICY_ID`: ID of the IKE policy.
- `--json`: Format output in JSON.

---

### `ibmcloud is ike-policy-create`
{: #ike-policy-create}

**Create an IKE policy.**

`ibmcloud is ike-policy-create IKE_POLICY_NAME AUTHENTICATION_ALGORITHM DH_GROUP ENCRYPTION_ALGORITHM IKE_VERSION [--key-lifetime KEY_LIFETIME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**
- `IKE_POLICY_NAME`: Name of the IKE policy.
- `AUTHENTICATION_ALGORITHM`: The authentication algorithm. Enumeration type: `md5`, `sha1`, `sha256`.
- `DH_GROUP`: The Diffie-Hellman group. Enumeration type: `2`, `5`, `14`.
- `ENCRYPTION_ALGORITHM`: The encryption algorithm. Enumeration type: `3des`, `aes128`, `aes256`.
- `IKE_VERSION`: The IKE protocol version. Enumeration type: `1`, `2`.
- `--key-lifetime`: The key lifetime in seconds. Maximum: 86400, Minimum: 300 (default: 28800).
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is ike-policy-delete`
{: #ike-policy-delete}

**Delete an IKE policy.**

`ibmcloud is ike-policy-delete IKE_POLICY_ID [-f, --force]`

**Options**

- `IKE_POLICY_ID`: ID of the IKE policy.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is ike-policy-update`
{: #ike-policy-update}

**Update an IKE policy.**

`ibmcloud is ike-policy-update IKE_POLICY_ID [--authentication_algorithm md5 | sha1 | sha256] [--dh-group 2 | 5 | 14] [--encryption-algorithm 3des | aes128 | aes256] [--ike-version 1 | 2] [--key-lifetime KEY_LIFETIME] [--name NEW_NAME] [--json]`

**Options**
- `IKE_POLICY_ID` ID of the IKE policy.
- `--name`: New name of the IKE policy.
- `--authentication-algorithm`: The authentication algorithm. Enumeration type: `md5`, `sha1`, `sha256`.
- `--dh-group`: The Diffie-Hellman group. Enumeration type: `2`, `5`, `14`.
- `--encryption-algorithm`: The encryption algorithm. Enumeration type: `3des`, `aes128`, `aes256`.
- `--ike-version`: The IKE protocol version. Enumeration type: `1`, `2`.
- `--key-lifetime`: The key lifetime in seconds. Maximum: 86400, Minimum: 300.
- `--json`: Format output in JSON.

---

### `ibmcloud is ike-policy-connections`
{: #ike-policy-connections}

**List all connections that use the IKE policy.**

`ibmcloud is ike-policy-connections IKE_POLICY_ID [--json]`

**Options**
- `IKE_POLICY_ID`: ID of the IKE policy.
- `--json`: Format output in JSON.


## IPsec Policies

### `ibmcloud is ipsec-policies`
{: #ipsec-policies}

**List all IPsec policies.**

`ibmcloud is ipsec-policies [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is ipsec-policy`
{: #ipsec-policy}

**View details of an IPsec policy.**

`ibmcloud is ipsec-policy IPSEC_POLICY_ID [--json]`

**Options**
- `IPSEC_POLICY_ID`: ID of the IPsec policy.
- `--json`: Format output in JSON.

---

### `ibmcloud is ipsec-policy-create`
{: #ipsec-policy-create}

**Create an IPsec policy.**

`ibmcloud is ipsec-policy-create IPSEC_POLICY_NAME AUTHENTICATION_ALGORITHM ENCRYPTION_ALGORITHM PFS [--key-lifetime KEY_LIFETIME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**
- `IPSEC_POLICY_NAME`: Name of the IPsec policy.
- `AUTHENTICATION_ALGORITHM`: The authentication algorithm. Enumeration type: `md5`, `sha1`, `sha256`.
- `ENCRYPTION_ALGORITHM`: The encryption algorithm. Enumeration type: `3des`, `aes128`, `aes256`.
- `PFS`: Perfect Forward Secrecy. Enumeration type: disabled, `group_2`, `group_5`, `group_14`.
- `--key-lifetime`: The key lifetime in seconds. Maximum: 86400, Minimum: 300 (default: 3600).
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is ipsec-policy-delete`
{: #ipsec-policy-delete}

**Delete an IPsec policy.**

`ibmcloud is ipsec-policy-delete IPSEC_POLICY_ID [-f, --force]`

**Options**

- `IPSEC_POLICY_NAME`: Name of the IPsec policy.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is ipsec-policy-update`
{: #ipsec-policy-update}

**Update an IPsec policy.**

`ibmcloud is ipsec-policy-update IPSEC_POLICY_ID [--authentication_algorithm md5 | sha1 | sha256] [--pfs disabled | group_2 | group_5 | group_14] [--encryption-algorithm 3des | aes128 | aes256] [--key-lifetime KEY_LIFETIME] [--name NEW_NAME] [--json]`

**Options**
- `IPSEC_POLICY_ID`: ID of the IPsec policy.
- `--name`: New name of the IPsec policy.
- `--authentication-algorithm`: The authentication algorithm. Enumeration type: `md5`, `sha1`, `sha256`.
- `--pfs`: Perfect Forward Secrecy. Enumeration type: `disabled`, `group_2`, `group_5`, `group_14`.
- `--encryption-algorithm`: The encryption algorithm. Enumeration type: `3des`, `aes128`, `aes256`.
- `--key-lifetime`: The key lifetime in seconds. Maximum: 86400, Minimum: 300.
- `--json`: Format output in JSON.

---

### `ibmcloud is ipsec-policy-connections`
{: #ipsec-policy-connections}

**List all connections that use the IPsec policy.**

`ibmcloud is ipsec-policy-connections IPSEC_POLICY_ID [--json]`

**Options**
- `IPSEC_POLICY_NAME`: Name of the IPsec policy.
- `--json`: Format output in JSON.


## VPN Gateway Commands

This section contains commands available for working with VPN for VPC gateways.

### `ibmcloud is vpn-gateways`
{: #vpn-gateways}


**List all VPN gateways.**

`ibmcloud is vpn-gateways [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway`
{: #vpn-gateway}

**View details of a VPN gateway.**

`ibmcloud is vpn-gateway VPN_GATEWAY_ID [--json]`

**Options**
- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-create`
{: #vpn-gateway-create}

**Create a VPN gateway.**

`ibmcloud is vpn-gateway-create VPN_GATEWAY_NAME SUBNET_ID [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**
- `VPN_GATEWAY_NAME`: Name of the VPN gateway.
- `SUBNET_ID`: The unique identifier for this subnet.
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-delete`
{: #vpn-gateway-delete}

**Delete a VPN gateway.**

`ibmcloud is vpn-gateway-delete VPN_GATEWAY_ID [-f, --force]`

**Options**

- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is vpn-gateway-update`
{: #vpn-gateway-update}

**Update a VPN gateway.**

`ibmcloud is vpn-gateway-update VPN_GATEWAY_ID [--name NEW_NAME] [--json]`

**Options**
- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `--name`: New name of the VPN gateway.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-connections`
{: #vpn-gateway-connections}

**List all VPN gateway connections.**

`ibmcloud is vpn-gateway-connections VPN_GATEWAY_ID [--json]`

**Options**
- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-connection-create`
{: #vpn-gateway-connection-create}

**Create a VPN gateway connection.**

`ibmcloud is vpn-gateway-connection-create CONNECTION_NAME VPN_GATEWAY_ID PEER_ADDRESS PRESHARED_KEY [--admin-state-up true | false] [--dead-peer-detection-action ACTION] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID]  [--local-cidr CIDR1 --local-cidr CIDR2 ...] [--peer-cidr CIDR1 --peer-cidr CIDR2 ...] [--json]`

**Options**
- `CONNECTION_NAME`: Name of the connection.
- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `PEER_ADDRESS`: The IP address of the peer VPN gateway.
- `PRESHARED_KEY`: The preshared key.
- `--admin-state-up`: If set to `false`, the VPN gateway connection is shut down. default is `false`.
- `--dead-peer-detection-action`: Dead Peer Detection actions. Enumeration type: `restart`, `clear`, `hold`, `none`.
- `--dead-peer-detection-interval`: Dead Peer Detection interval in seconds (default: 30).
- `--dead-peer-detection-timeout`: Dead Peer Detection timeout in seconds (default: 120).
- `--ike-policy`: ID of the IKE policy.
- `--ipsec-policy`: ID of the IPsec policy.
- `--local-cidr`: Local CIDR for this resource. This parameter can be specified multiple times to provision multiple local CIDRs.
- `--peer-cidr`: Peer CIDRs for this resource. This parameter can be specified multiple times to provision multiple peer CIDRs.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-connection`
{: #vpn-gateway-connection}

**View details of a VPN gateway connection.**

`ibmcloud is vpn-gateway-connection VPN_GATEWAY_ID CONNECTION_ID [--json]`

**Options**
- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `CONNECTION_ID`: ID of the connection.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-connection-delete`
{: #vpn-gateway-connection-delete}

**Delete a VPN gateway connection.**

`ibmcloud is vpn-gateway-connection-delete VPN_GATEWAY_ID CONNECTION_ID [-f, --force]`

**Options**

- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `CONNECTION_ID`: ID of the connection.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is vpn-gateway-connection-update`
{: #vpn-gateway-connection-update}

**Update a VPN gateway connection.**

`ibmcloud is vpn-gateway-connection-update VPN_GATEWAY_ID CONNECTION_ID [--admin-state-up true | false] [--dead-peer-detection-action ACTION] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID] [--peer-address ADDRESS] [--psk PSK] [--name NEW_NAME] [--json]`

**Options**
- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `CONNECTION_ID`: ID of the connection.
- `--admin-state-up`: If set to `false`, the VPN gateway connection is shut down. default is `false`.
- `--dead-peer-detection-action`: Dead Peer Detection actions. Enumeration type: `restart`, `clear`, `hold`, `none`.
- `--dead-peer-detection-interval`: Dead Peer Detection interval in seconds.
- `--dead-peer-detection-timeout`: Dead Peer Detection timeout in seconds.
- `--ike-policy`: ID of the IKE policy.
- `--ipsec-policy`: ID of the IPsec policy.
- `--peer-address`: The IP address of the peer VPN gateway.
- `--psk`: The preshared key.
- `--name`: New name of the connection.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-connection-local-cidr-delete`
{: #vpn-gateway-connection-local-cidr-delete}

**Remove a local CIDR from the VPN gateway connection.**

`ibmcloud is vpn-gateway-connection-local-cidr-delete VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [-f, --force]`

**Options**

- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `CONNECTION_ID`: ID of the connection.
- `PREFIX_ADDRESS`: The prefix address part of the CIDR.
- `PREFIX_LENGTH`: The prefix length part of the CIDR.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is vpn-gateway-connection-local-cidr-add`
{: #vpn-gateway-connection-local-cidr-add}

**Add a local CIDR to a VPN gateway connection.**

`ibmcloud is vpn-gateway-connection-local-cidr-add VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [--json]`

**Options**

- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `CONNECTION_ID`: ID of the connection.
- `PREFIX_ADDRESS`: The prefix address part of the CIDR.
- `PREFIX_LENGTH`: The prefix length part of the CIDR.
- `--json`: Format output in JSON.

---

### `ibmcloud is vpn-gateway-connection-peer-cidr-delete`
{: #vpn-gateway-connection-peer-cidr-delete}

**Remove a peer CIDR from the VPN gateway connection.**

`ibmcloud is vpn-gateway-connection-peer-cidr-delete VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [-f, --force]`

**Options**

- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `CONNECTION_ID`: ID of the connection.
- `PREFIX_ADDRESS`: The prefix address part of the CIDR.
- `PREFIX_LENGTH`: The prefix length part of the CIDR.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is vpn-gateway-connection-peer-cidr-add`
{: #vpn-gateway-connection-peer-cidr-add}

**Add a peer CIDR to a VPN gateway connection.**

`ibmcloud is vpn-gateway-connection-peer-cidr-add VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [--json]`

**Options**

- `VPN_GATEWAY_ID`: ID of the VPN gateway.
- `CONNECTION_ID`: ID of the connection.
- `PREFIX_ADDRESS`: The prefix address part of the CIDR.
- `PREFIX_LENGTH`: The prefix length part of the CIDR.
- `--json`: Format output in JSON.


## Load Balancer Commands
{: #load-balancers}

This section gives details about the CLI commands available for working with load balancers, listeners, and pools.

## Load Balancer

### `ibmcloud is load-balancers`
{: #load-balancers-cli}

**List all load balancers.**

`ibmcloud is load-balancers [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer`
{: #load-balancer}

**View details of a load balancer.**

`ibmcloud is load-balancer LOAD_BALANCER_ID [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-create`
{: #load-balancer-create}

**Create a load balancer.**

`ibmcloud is load-balancer-create LOAD_BALANCER_NAME LOAD_BALANCER_TYPE (--subnet SUBNET_ID1 --subnet SUBNET_ID2 ...) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**

- `LOAD_BALANCER_NAME`: Name of the load balancer.
- `LOAD_BALANCER_TYPE`: Type of the load balancer, public or private.
- `--subnet`: ID of the subnets to provision this load balancer. This parameter can be specified multiple times to provision multiple subnets.
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-delete`
{: #load-balancer-delete}

**Delete a load balancer.**

`ibmcloud is load-balancer-delete LOAD_BALANCER_ID [-f, --force]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is load-balancer-update`
{: #load-balancer-update}

**Update a load balancer.**

`ibmcloud is load-balancer-update LOAD_BALANCER_ID [--name NEW_NAME] [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `--name`: New name of the Load balancer.
- `--json`: Format output in JSON.

---

## Load Balancer Listener

### `ibmcloud is load-balancer-listeners`
{: #load-balancer-listeners}

**List all load balancer listeners.**

`ibmcloud is load-balancer-listeners LOAD_BALANCER_ID [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-listener`
{: #load-balancer-listener}

**View details of a load balancer listener.**

`ibmcloud is load-balancer-listener LOAD_BALANCER_ID LISTENER_ID [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `LISTENER_ID`: ID of the listener.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-listener-create`
{: #load-balancer-listener-create}

**Create a load balancer listener.**

`ibmcloud is load-balancer-listener-create LOAD_BALANCER_ID PORT PROTOCOL [--certificate-instance CERTIFICATE_INSTANCE_CRN] [--connection-limit LIMIT] [--default-pool DEFAULT_POOL_ID] [--policies LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE] [--json]`

**Options**
- `LOAD_BALANCER_NAME`: Name of the load balancer.
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `PORT`: The listener port number.
- `PROTOCOL`: The listener protocol. Enumeration type: `http`, `https`, `tcp`.
- `--certificate-instance-crn`: CRN of the certificate instance. Required when protocol is HTTPS.
- `--connection-limit`: The connection limit of the listener.
- `--default-pool`: ID of the default pool.
- `--policies`: LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE, listener policies in json or json file.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-listener-delete`
{: #load-balancer-listener-delete}

**Delete a load balancer listener.**

`ibmcloud is load-balancer-listener-delete LOAD_BALANCER_ID LISTENER_ID [-f, --force]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `LISTENER_ID`: ID of the listener.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is load-balancer-listener-update`
{: #load-balancer-listener-update}

**Update a load balancer listener.**

`ibmcloud is load-balancer-listener-update LOAD_BALANCER_ID LISTENER_ID [--certificate-instance CERTIFICATE_INSTANCE_ID] [--connection-limit LIMIT] [--port PORT] [--protocol http | https | tcp] [--default-pool DEFAULT_POOL_ID] [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `LISTENER_ID`: ID of the listener.
- `--certificate-instance-crn`: CRN of the certificate instance.
- `--connection-limit`: The connection limit of the listener.
- `--default-pool`: ID of the default pool.
- `--protocol`: The listener protocol. Enumeration type: `http`, `https`, `tcp`.
- `--port`: The listener port.
- `--json`: Format output in JSON.

---

## Load Balancer Pools

### `ibmcloud is load-balancer-pools`
{: #load-balancer-pools}

**List all pools of a load balancer.**

`ibmcloud is load-balancer-pools LOAD_BALANCER_ID [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool`
{: #load-balancer-pool}

**View details of a load balancer pool.**

`ibmcloud is load-balancer-pool LOAD_BALANCER_ID POOL_ID [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool-create`
{: #load-balancer-pool-create}

**Create a load balancer pool.**

`ibmcloud is load-balancer-pool-create POOL_NAME LOAD_BALANCER_ID ALGORITHM PROTOCOL HEALTH_DELAY HEALTH_RETRIES HEALTH_TIMEOUT HEALTH_TYPE [--health-monitor-url URL][--health-monitor-port PORT][--session-persistence-type TYPE] [--json]`

**Options**
- `POOL_NAME`: Name of the pool.
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `ALGORITHM`: The load balancing algorithm. Enumeration type: `round_robin`, `weighted_round_robin`, least_connections.
- `PROTOCOL`: The pool protocol. Enumeration type: `http`, `tcp`.
- `HEALTH_DELAY`: The health check interval in seconds. The interval must be greater than the timeout value.
- `HEALTH_RETRIES`: The health check maximum retries.
- `HEALTH_TIMEOUT`: The health check timeout in seconds.
- `HEALTH_TYPE`: The pool protocol. Enumeration type: `http`, `tcp`.
- `--health-monitor-url`: The health check url. This option is applicable only to `http` type of HEALTH_TYPE.
- `--session-persistence-type`: The session persistence type, Enumeration type: `source_ip`, `http_cookie`, app_cookie.
- `--health-monitor-port`: The health check port number.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool-delete`
{: #load-balancer-pool-delete}

**Delete a pool from a load balancer.**

`ibmcloud is load-balancer-pool-delete LOAD_BALANCER_ID POOL_ID [-f, --force]`

**Options**
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is load-balancer-pool-update`
{: #load-balancer-pool-update}

**Update a pool of a load balancer.**

`ibmcloud is load-balancer-pool-update LOAD_BALANCER_ID POOL_ID [--algorithm round_robin | weighted_round_robin | least_connections] [--health-delay DELAY --health-max-retries RETRIES --health-timeout TIMEOUT --health-type TYPE --health-monitor-url URL] [--health-monitor-port PORT] [--protocol http | tcp] [--session-persistence-type TYPE] [--name NEW_NAME] [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `--algorithm`: The load balancing algorithm. Enumeration type: `round_robin`, `weighted_round_robin`, `least_connections`.
- `--health-delay`: The health check interval in seconds. Interval must be greater than timeout value.
- `--health-max-retries`: The health check max retries.
- `--health-monitor-url`: The health check url. This option is applicable only to `http` type of `--health-type`.
- `--health-timeout`: The health check timeout in seconds.
- `--health-type`: The pool protocol. Enumeration type: `http`, `tcp`.
- `--health-monitor-port`: The health check port number.
- `--session-persistence-type`: The session persistence type, Enumeration type: `source_ip`, `http_cookie`, `app_cookie`.
- `--session-persistence-cookie-name`: Session persistence cookie name. This option is applicable only to `--session-persistence-type`.
- `--protocol`: The pool protocol. Enumeration type: `http`, `tcp`.
- `--name`: The new name of the pool.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool-members`
{: #load-balancer-pool-members}

**List all the members of a load balancer pool.**

`ibmcloud is load-balancer-pool-members LOAD_BALANCER_ID POOL_ID [--json]`

**Options**

- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool-member`
{: #load-balancer-pool-member}

**View details of load balancer pool member.**

`ibmcloud is load-balancer-pool-member LOAD_BALANCER_ID POOL_ID MEMBER_ID [--json]`

**Options**
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `MEMBER_ID`: ID of the member.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool-member-create`
{: #load-balancer-pool-member-create}

**Create a load balancer pool member.**

`ibmcloud is load-balancer-pool-member-create LOAD_BALANCER_ID POOL_ID PORT TARGET_ADDRESS [--weight WEIGHT] [--json]`

**Options**
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `PORT`: The port number of the application running in the server member.
- `TARGET_ADDRESS`: The IP address of the pool member.
- `--weight`: Weight of the server member. This option takes effect only when the load balancing algorithm of its belonging pool is `weighted_round_robin`.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool-member-update`
{: #load-balancer-pool-member-update}

**Update a member of a load balancer pool.**

`ibmcloud is load-balancer-pool-member-update LOAD_BALANCER_ID POOL_ID MEMBER_ID [--port PORT] [--target-address TARGET_ADDRESS] [--weight WEIGHT] [--json]`

**Options**
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `MEMBER_ID`: ID of the member.
- `--target-address`: The IP address of the pool member.
- `--weight`: Weight of the server member. This option takes effect only when the load balancing algorithm of its belonging pool is `weighted_round_robin`.
- `--port`: The port number of the application running in the server member.
- `--json`: Format output in JSON.

---

### `ibmcloud is load-balancer-pool-member-delete`
{: #load-balancer-pool-member-delete}

**Delete a member from a load balancer pool.**

`ibmcloud is load-balancer-pool-member-delete LOAD_BALANCER_ID POOL_ID MEMBER_ID [-f, --force]`

**Options**
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `POOL_ID`: ID of the pool.
- `MEMBER_ID`: ID of the member.
- `--force, -f`: Delete without confirmation.

---

### `ibmcloud is load-balancer-statistics`
{: #load-balancer-statistics}

**List all statistics of a load balancer.**

`ibmcloud is load-balancer-statistics LOAD_BALANCER_ID [--json]`

**Options**
- `LOAD_BALANCER_ID`: ID of the load balancer.
- `--json`: Format output in JSON.

## Storage CLI commands
{: #storage}

This section gives details about the CLI commands available for working with block storage volumes.

## Volume Profile

### `ibmcloud is volume-profile`

**View details of a volume profile.**

`ibmcloud is volume-profile PROFILE_NAME [--json]`

**Options**

- `PROFILE_NAME`: Name of the volume profile.  Volume profile names are 10iops-tier, 5iops-tier, general-purpose, and custom.
- `--json`: Format output in JSON.

---

### `ibmcloud is volume-profiles`

**List all volume profiles.**

`ibmcloud is volume-profiles [--json]`

**Options**

- `--json`: Format output in JSON.


## Volume

### `ibmcloud is volume`

**View details of a volume.**

`ibmcloud is volume VOLUME_ID [--json]`

**Options**

- `VOLUME_ID`: ID of the volume.
- `--json`: Format output in JSON.

---

### `ibmcloud is volumes`

**List all volumes.**

`ibmcloud is volumes [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud is volume-create`

**Create a volume.**

`ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]`

**Options**

- `VOLUME_NAME`: Name of the volume you specify.
- `PROFILE_NAME`: Name of the volume profile, for example, general-purpose.
- `ZONE_NAME`: Name of zone.  For example, us-south-1.
- `--capacity`: Capacity of the volume in GB, from 10 GB to 20,000 GB. Defaults to 100 GB.
- `--iops`: Input/Output Operations Per Second for the volume.
- `--encryption-key`: The CRN (Cloud Resource Name) of the root key in IBM Key Protect service.
- `--resource-group-id`: ID of the resource group. This option is exclusive with --resource-group-name.
- `--resource-group-name`: Name of the resource group. This option is exclusive with --resource-group-id.
- `--json`: Format output in JSON.

---

### `ibmcloud is volume-delete`

**Delete a volume.**

`ibmcloud is volume-delete VOLUME_ID [-f, --force]`

**Options**

- `VOLUME_ID`: ID of the volume.
- `--force, -f`: Force the operation without confirmation.

---

### `ibmcloud is volume-update`

**Update a volume.

`ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]`

**Options**

- `VOLUME_ID`: ID of the volume.
- `--name`: New name of the volume.
- `--json`: Format output in JSON.

