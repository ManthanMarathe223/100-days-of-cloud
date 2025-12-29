# Day 02 – Security Groups, VPC, and Networking Basics

## What I did
- Created a security group named `datacenter-sg`
- Added inbound rule for HTTP (port 80) from `0.0.0.0/0`
- Added inbound rule for SSH (port 22) from `0.0.0.0/0`
- Used the Default VPC -> which is for beginners

## What I learned

### What is a Security Group?
- A security group acts as a firewall for EC2 instances
- It controls which network traffic is allowed to reach the server
- Inbound rules define allowed traffic; outbound rules define allowed responses
- Security groups are stateful (responses are automatically allowed - means the outbounds)

### Why these rules?
- HTTP (80): Allows public web traffic
- SSH (22): Allows administrators to log in using key pairs
- `0.0.0.0/0` means access from anywhere on the internet (okay for labs, unsafe for production)

---

### What is EC2?
- EC2 stands for Elastic Compute Cloud
- It is a virtual computer/server hosted in AWS
- It can run Linux or Windows and is paid per usage
- Elastic means it can scale up or down easily

---

### What is a VPC?
- VPC stands for Virtual Private Cloud
- It is a private, isolated network created inside AWS
- All AWS resources like EC2, subnets, and security groups live inside a VPC
- AWS provides a default VPC for beginners

---

### What is a Subnet?
- A subnet is a smaller network inside a VPC
- It is used to organize and isolate resources
- Public subnet → allows internet access
- Private subnet → no direct internet access

---

### Security Group vs NACL
- Security Group:
  - Applied to EC2 instances
  - Acts as a server-level firewall
  - Stateful
- NACL (Network ACL):
  - Applied to subnets
  - Acts as a network-level firewall
  - Stateless (inbound and outbound rules required)

## One-line memory rules
- No security group = no traffic
- EC2 = virtual server
- VPC = private network
- Subnet = smaller network inside VPC
- Traffic passes NACL first, then Security Group

## One doubt:
- When should NACLs be preferred over security groups in real systems?

## Proof of Work: Created Security Group Named -> datacenter-sg
<img width="1918" height="926" alt="image" src="https://github.com/user-attachments/assets/ebd3e499-209d-4e9f-85a2-d6b2e8338608" />
