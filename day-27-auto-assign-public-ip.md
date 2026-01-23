# Day 27 – Public VPC and EC2

## What I did
- Created a public VPC `devops-pub-vpc`
- Created a public subnet `devops-pub-subnet` with auto public IP assignment
- Launched an EC2 instance `devops-pub-ec2` inside the VPC
- Configured security group to allow SSH access from the internet

## What I learned
- Public VPCs require an Internet Gateway
- Public subnets auto-assign public IPs to resources
- Route tables control internet access
- Security groups control who can access EC2 instances

## One-line takeaway
> Public access in AWS requires proper networking, routing, and security rules.

## Auto Assigning Public IP:
- Its different from regular IP assignments
- If 'auto assign public ip' is not enabled then the ec2 gets the default private ip
  and is not accessible publically
- After creating VPC and while creating subnet we see this option
- Assign an internet gateway to your VPC's routing table
- So that the subnet is made public
- When we create a security group select the VPC for which we are creating the 'sg'
- So that any instance created in that VPC gets the same security group assignment
