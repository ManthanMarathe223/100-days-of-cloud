# Day 05 – EBS (Elastic Block Storage) Volume

## What I did
- Created an EBS volume named `datacenter-volume`
- Set volume type to gp3 (General Purpose SSD v3)
- Set volume size to 2 GiB

## What I learned
- EBS volumes act as virtual hard disks for EC2
- EBS is Elastic Block Storage like Pen Drive or Hard Disk
- gp3 is a general-purpose SSD v3 volume type
- GiB means Gibibytes
- GiB (Gibi) uses powers of 2 (1024), while GB (Giga) uses powers of 10 (1000).
- EBS volumes are independent of EC2 instances
- A volume must be in the same AZ as the EC2 it attaches to
