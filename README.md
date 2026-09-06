# Azure Cloud Infrastructure Lab

## Project Overview

This project documents the deployment of a small cloud infrastructure environment in Microsoft Azure. The goal was to gain hands-on experience with Azure virtual networking, Linux virtual machines, network segmentation, security controls, and SSH administration.

## Architecture

The environment uses a single Azure Virtual Network with separate subnets for server and management resources.

### Network

- **Virtual Network:** `vnet-cloudlab`
- **Server Subnet:** `snet-servers` — `10.10.10.0/24`
- **Management Subnet:** `snet-management` — `10.10.30.0/24`

### Virtual Machines

**srv-linux-01**
- Ubuntu Server 24.04 LTS
- Deployed in `snet-servers`
- Private IP: `10.10.10.4`
- No direct public exposure

**vm-mgmt-01**
- Ubuntu Server 24.04 LTS
- Deployed in `snet-management`
- Public IP assigned for remote administration
- SSH key authentication

## Security

A Network Security Group (NSG) was configured for the management VM.

Inbound SSH access on TCP port 22 is restricted to an authorized public IP address rather than being exposed to the entire internet.

The server VM does not have a public IP address, reducing direct internet exposure.

## Cost Management

Azure VM auto-shutdown was configured to prevent unnecessary compute usage and reduce lab costs.

## Skills Demonstrated

- Microsoft Azure
- Azure Virtual Machines
- Azure Virtual Networks
- Subnetting
- Network Security Groups
- Linux administration
- SSH key authentication
- Network segmentation
- Cloud security fundamentals
- Azure cost management

## Future Improvements

- Configure private SSH access from the management VM to the server VM
- Deploy additional Linux services
- Implement Azure monitoring
- Recreate the environment using Infrastructure as Code
- Add Terraform or Bicep templates
