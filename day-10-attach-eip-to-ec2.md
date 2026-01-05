# Day 10 – Elastic IP Association

## What I did
- Verified the existing Elastic IP `nautilus-ec2-eip`
- Associated the Elastic IP with the EC2 instance `nautilus-ec2`
- Ensured the Elastic IP shows as **associated** with the instance

## What I learned
- Allocating an Elastic IP only reserves a public IP address
- Associating an Elastic IP attaches it to an EC2 instance
- The task is complete only when the Elastic IP shows an associated instance
- AWS Console may use confusing terms like “Allocate”, so the **final state matters**
- Multiple console paths can be used to associate an Elastic IP, but the result must be correct

## Key clarification
- **Allocated ≠ Associated**
- The lab checks whether `nautilus-ec2-eip` is attached to `nautilus-ec2`, not how it was done

## One-line memory rule
- An Elastic IP is useful only when it is **associated** with a resource.

## Proof of Work:
<img width="1918" height="927" alt="image" src="https://github.com/user-attachments/assets/99593747-acc8-4b51-9193-fd091bab5660" />
