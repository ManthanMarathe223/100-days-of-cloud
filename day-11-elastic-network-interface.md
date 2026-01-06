# Day 11 – Elastic Network Interface (ENI)

## What I did
- Attached the existing network interface `devops-eni`
- Connected it to the EC2 instance `devops-ec2`
- Verified the ENI status is attached
- Ensured the instance initialization completed successfully

## What I learned
- ENI is a virtual network interface for EC2
- EC2 instances can have multiple network interfaces
- ENIs allow advanced networking configurations
- Device index 0 is reserved for the primary interface

- An EC2 instance does not directly talk to the network.
    - EC2 → ENI → Subnet → VPC → Internet
- No ENI = no network
- EC2 always has at least 1 ENI

## In simple words
- ENI is a virtual network card for an EC2 instance
  - Just like:
  - Your laptop has a Wi-Fi card
  - Your desktop can have multiple network cards
