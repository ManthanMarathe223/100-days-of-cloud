# Day 26 – EC2 Web Server with User Data

## What I did
- Created an EC2 instance named `nautilus-ec2` using Ubuntu AMI
- Used a user data script to install and start Nginx
- Configured security group to allow HTTP traffic on port 80

## What I learned
- User data scripts automate instance configuration at launch
- Nginx can be installed and started automatically
- Security groups control public access to EC2 instances

## One-line takeaway
> User data helps bootstrap servers without manual configuration.

## User Data Script to install Nginx
```cmd
#!/bin/bash
apt update -y
apt install nginx -y
systemctl start nginx
systemctl enable nginx
```

### Explanation:

* `#!/bin/bash`
  → Tells the system to run this script using the **bash shell**.

* `apt update -y`
  → Updates the package list so Ubuntu knows the latest available software.
  * **`apt`** (Advanced Package Tool)
    → Ubuntu’s **package manager** used to install, update, and remove software.

* `apt install nginx -y`
  → Installs the **Nginx web server** without asking for confirmation.

* `systemctl start nginx`
  → Starts the Nginx service immediately.
  * **`systemctl`** (System Contrl)
    → Linux **service manager** used to start, stop, and control background services (like Nginx).

* `systemctl enable nginx`
  → Ensures Nginx starts **automatically on every reboot**.
