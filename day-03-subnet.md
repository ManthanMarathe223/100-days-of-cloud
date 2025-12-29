# Day 03 – Subnet

## What I did
- Created a subnet named `xfusion-subnet`
- Created it under the default VPC
- Assigned an IPv4 CIDR block

## CIDR (Classless Inter-Domain Routing):
- CIDR is just a way to define a range of IP addresses
- CIDR defines “how big” a network is — nothing more.
- AWS needs to know:
  - How many servers you can place
  - Which IP belongs to which subnet
  - How routing works internally

## What I learned
- Subnets are smaller networks inside a VPC
- EC2 instances must be launched inside a subnet
- Subnets help organize and isolate cloud resources

## One doubt
- How does AWS decide if a subnet is public or private?

# Work Proof: Created a Subnet inside Default VPC
<img width="1918" height="927" alt="image" src="https://github.com/user-attachments/assets/11006e77-6c20-46c1-bec1-3e583b86e0d0" />
