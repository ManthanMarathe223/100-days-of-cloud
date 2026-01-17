# Day 21 – EC2 & Elastic IP (Lab Debugging)

## What I did
- Created an EC2 instance
- Created an Elastic IP and associated it with the instance
- Faced a validation error in the first attempt
- Fixed the issue and completed the task successfully

## What I learned
- EC2 requires a key pair by default; key pair name may not matter for the task
- Lab validation often checks the **Name tag value** of resources
- A mismatch in tag values can cause task failure even if resources exist
- Creating extra resources usually does not affect lab results

## Key takeaway
- Always match **exact tag values** mentioned in the task

## One-line rule
> In labs, correctness of names and tags matters more than how you created the resource.

## Proof of Work: 
<img width="1910" height="481" alt="image" src="https://github.com/user-attachments/assets/45cadb7d-fcec-4413-9da2-ffb722787c4f" />
