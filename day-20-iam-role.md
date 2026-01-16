# Day 20 – IAM Role (EC2)

## What I did
- Created an IAM role named `iamrole_javed`
- Selected AWS service as trusted entity
- Chose EC2 as the use case
- Attached the policy `iampolicy_javed`

## What I learned
- IAM roles are used by AWS services, not humans
- EC2 assumes roles to access AWS services securely
- Roles eliminate the need for access keys inside instances

## One-line rule
> Use IAM roles for AWS services instead of IAM users.

