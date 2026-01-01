# Day 06 – EC2 Instance

## What I did
- Launched an EC2 instance named `xfusion-ec2`
- Used Amazon Linux AMI
- Selected instance type t2.micro
- Created a new RSA key pair `xfusion-kp`
- Attached the default security group

## What I learned
- EC2 instances require AMI, instance type, key pair, and security group
- Key pairs are used for secure SSH access
- Security groups control network traffic to EC2
- Default security group allows basic internal communication

## t2.micro

* t2.micro = small-sized virtual computer
* Instance type = hardware size
* `t2` → generation
* `micro` → very small

---

## AMI

### Full form

**AMI = Amazon Machine Image**

- AMI = operating system template for EC2
Contains:
* OS (Amazon Linux, Ubuntu, etc.)
* Basic configs
---

## RSA

- RSA = encryption algorithm used in key pairs
Used for:
* Secure SSH login
* Encrypting communication

In AWS:

* RSA keys prove **you are authorized**
* Passwords are avoided


## Proof Of Work: Created EC2 Instance Fully
<img width="1918" height="643" alt="image" src="https://github.com/user-attachments/assets/d762cd3f-0844-407a-82b1-24e4a6dd2db6" />
