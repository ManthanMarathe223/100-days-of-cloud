# Day 01 – EC2 Key Pair

## What I did
- Created an EC2 key pair named `datacenter-kp`
- Used RSA key type
- Created the key in the `us-east-1` region
- Downloaded the private key file

## What I learned
- AWS does not allow password-based login for EC2 instances by default
- Key pairs are used for secure, key-based authentication
- A key pair acts like a physical key to access a cloud server
- EC2 key pairs must be created inside AWS (not using local ssh-keygen)

## Important Concepts
- EC2 = Elastic Compute Cloud (virtual server in AWS)
- Key pair = Secure way to log in to EC2
- IAM users provided in labs have limited permissions and time-bound access

## One doubt
- How does AWS validate the key during EC2 login?
