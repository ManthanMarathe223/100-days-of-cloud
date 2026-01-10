# Day 15 – EBS Snapshot

## What I did
- Created a snapshot from the EBS volume `datacenter-vol`
- Named the snapshot `datacenter-vol-ss`
- Added description `datacenter Snapshot`
- Waited until the snapshot status became Completed

## What I learned
- A snapshot is a backup of an EBS volume that includes both
- the volume structure and all data stored on it at that time.
- Snapshots are backups of EBS volumes
- Snapshots are incremental and stored by AWS
- New EBS volumes can be created from snapshots
- Snapshot must be in Completed state before it can be used
