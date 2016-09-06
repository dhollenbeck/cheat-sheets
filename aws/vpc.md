# Virtual Private Cloud (VPC)

* A VPC is your network within AWS, but is private and controlled by you.
* A VPC is the network in which your ec2 instances reside.
* A VPC resides within an AWS region.
* A VPC which resides in a single AWS region you access it via subnets in each availability zone.

https://www.youtube.com/watch?v=5_bQ6Dgk6k8

## Step 1: Choosing IP Address Ranges

* Choose RFC1918 range which is a standard for private address ranges (172.31.0.0/16).
* Use a mask (address range size) of 16 which is the largest supported by AWS which allocates 64K IP addresses.
* Choose address range which does not conflict with another network you will connect.

## Step 2: Setup Subnets

You divide up your VPC into subnets. You want your VPC to be available in each Availability Zone (AZ), therefore create a subnet for each AZ in the region.

* eu-west-1a: 172.31.0.0/24
* eu-west-1b: 172.31.1.0/24
* eu-west-1c: 172.31.2.0/24

Slash 24 gives you 251 addresses in the subnet. The low 4 addresses are resevered by AWS.
  
## Step 3: Create a route to the Internet

The VPC comes with a route table. The route table has a list of rules of where the traffic goes.

### Outbound 
* The default route routes local traffic locally (172.31.0.0/16 => local). Therefore, no traffic can get out of the VPC.
* Outbound: You can attach an Internet Gateway (IGW) and route traffic to it (0.0.0.0/0 => IGW).

### Inbound

You route inbound traffic via network ACLs and security groups.

* Network ACL: state-less firewall. 
* Security Groups: stateful firewall.

Security groups are the recommended way of managing inbound and outbound traffic.

## Step 4 Connectivity Options for VPCs



