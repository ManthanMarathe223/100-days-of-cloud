# Day 29 – VPC Peering & Connectivity Test

## Objective
- Enable communication between a public EC2 and a private EC2 using VPC Peering
- Verify connectivity by pinging the private EC2 from the public EC2

---

## What was configured
- VPC Peering between **Default VPC** and **xfusion-private-vpc**
- Created VPC Peering and accepted request
- Route tables to access VPC Peering, updated on both VPCs
- Security groups updated to allow required traffic
- SSH access enabled to the public EC2 from aws-client
- ICMP enabled to test connectivity

---

## Key AWS Console Steps (to access Public EC2)

### Connect to Public EC2 via AWS Console
1. AWS Console → **EC2**
2. Select **xfusion-public-ec2**
3. Click **Connect**
4. Choose **EC2 Instance Connect**
5. Username: `ec2-user`
6. Click **Connect**

---

## Commands Used

### On aws-client (copy SSH public key)
```bash
cat /root/.ssh/id_rsa.pub
````

### On Public EC2 (add SSH key)

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
nano ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

# SSH Key Setup – Command Significance

- `mkdir -p ~/.ssh`  
  → Creates the `.ssh` directory if it doesn’t exist; required to store SSH keys securely.

- `chmod 700 ~/.ssh` (change mode)
    - 700 (read, write, and execute)
    - The chmod command in Linux is used to change the access permissions (or mode) of file system objects (files and directories)
  → Gives full access to the owner and blocks others; SSH refuses insecure directories.

- `nano ~/.ssh/authorized_keys`
    - The chmod command in Linux is used to change the access permissions (or mode) of file system objects (files and directories)
  → Opens the file where allowed public SSH keys are stored for login access.

- `chmod 600 ~/.ssh/authorized_keys`
    - 600 only the file's owner can read and write to the file
  → Restricts the file to owner-only access; required for SSH authentication to work.

## Why these permissions matter
SSH enforces strict permissions for security.  
If permissions are too open, SSH **denies login even with a valid key**.

### From aws-client (test SSH to public EC2)

```bash
ssh ec2-user@<public-ec2-public-ip>
```

---

## Test Connectivity (from Public EC2)

```bash
ping <private-ec2-private-ip>
```

✅ Successful ping confirms VPC Peering and routing are working.

---

## One-line takeaway

> **VPC Peering + correct routes + SG rules enable private communication across VPCs.**
