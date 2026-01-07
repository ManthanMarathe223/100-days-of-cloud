# Day 12 – EBS Volume Attachment

## What I did
- Attached the existing EBS(Elastic Block Store) volume `datacenter-volume`
- Connected it to the EC2 instance `datacenter-ec2`
- Set the device name to `/dev/sdb`
- Verified the volume state changed to In-use

## What I learned
- EBS volumes are independent storage resources
- Volumes must be attached to EC2 to be used
- Device names define how disks are presented to the OS
- Attaching a volume does not automatically format or mount it
- EBS can exist alone, but data is usable only when attached to EC2.
