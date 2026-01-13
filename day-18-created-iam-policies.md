# Day 18 – IAM Policy (Read-only EC2)

## What I did
- Created a custom IAM policy named `iampolicy_kareem`
- Defined the policy using JSON
- Allowed read-only access to EC2 resources

## What I learned
- IAM policies define what actions are allowed or denied
- Read-only access in AWS is provided using `Describe` actions
- EC2 read-only access allows viewing instances, AMIs, and snapshots
- `Resource: "*"` is required for EC2 Describe actions
- An empty Action list means no permissions are granted

## Key takeaway
- **Describe actions = view-only permissions**

## One-line rule
> IAM policies control permissions; without actions, users can do nothing.
