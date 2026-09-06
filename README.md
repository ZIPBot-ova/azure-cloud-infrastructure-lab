# Azure Cloud Infrastructure Lab

This is a lab I built to get more hands-on experience with Microsoft Azure and cloud networking.

The goal was to build a small Azure network from scratch, deploy Linux servers into separate subnets, and securely connect to the environment using SSH.

## What I Built

I created an Azure virtual network called `vnet-cloudlab` and separated the environment into different subnets:

- `snet-servers` - 10.10.10.0/24
- `snet-management` - 10.10.30.0/24

I deployed two Ubuntu Server 24.04 VMs.

### srv-linux-01

This is my internal Linux server.

- Located on the server subnet
- Private IP: `10.10.10.4`
- No public IP

### vm-mgmt-01

This VM is used to access and manage the environment.

- Located on the management subnet
- Has a public IP for remote access
- Uses SSH key authentication

## Network Security

I created a Network Security Group for the management VM and configured an inbound rule for SSH (TCP 22).

Instead of allowing SSH from anywhere on the internet, I restricted the rule to my public IP.

One issue I ran into was getting the NSG rule configured correctly. I had to troubleshoot the source address, source port range, and rule priority before Azure would accept the configuration.

## What I Learned

This lab helped me get a better understanding of:

- Azure VNets and subnets
- Public vs private IP addresses
- Network Security Groups
- Inbound security rules
- SSH key authentication
- Deploying and managing Linux VMs in Azure
- Basic Azure cost management using auto-shutdown

## Next Steps

Next I want to configure the management VM so I can use it to access the internal Linux server without exposing the server directly to the internet.
