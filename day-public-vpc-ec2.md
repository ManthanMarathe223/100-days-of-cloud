# Day 28 – Public VPC and EC2

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
