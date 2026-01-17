
# Day 22 – Passwordless SSH from aws-client to EC2

## Goal of the Task
- Create an EC2 instance named `nautilus-ec2`
- Allow passwordless SSH access to the EC2 instance **from aws-client**
- Use SSH keys created on aws-client
- Avoid AWS-managed SSH access for final login

---

## High-Level Concept (Before Commands)

- **aws-client** = jump / landing host
- **EC2** = remote server
- **SSH key-based login** requires:
  - Private key → stays on client (aws-client)
  - Public key → added to server (`authorized_keys`)

AWS key pairs are only used for **initial (bootstrap) access**.

---

## Step 1 – Create SSH Key on aws-client (Final Access Key)

```bash
ssh-keygen -t rsa -b 2048 -f /root/.ssh/id_rsa -N ""
````

### Command breakdown

* `ssh-keygen` → tool to create SSH keys
* `-t rsa` → use RSA encryption
* `-b 2048` → key size (secure default)
* `-f /root/.ssh/id_rsa` → file path for private key
* `-N ""` → empty passphrase (required for automation)

### Result

* `/root/.ssh/id_rsa` → private key (DO NOT SHARE)
* `/root/.ssh/id_rsa.pub` → public key (to be copied to EC2)

---

## Step 2 – Create Temporary Key for EC2 Bootstrap

```bash
ssh-keygen -t rsa -b 2048 -f ~/ec2-temp -N ""
```

### Why this key exists

* AWS EC2 **forces** a key pair at launch
* This key is used **only once** to get inside EC2
* It is NOT the final access key

---

## Step 3 – Import Temporary Public Key into AWS

```bash
cat ~/ec2-temp.pub
```

* Copy output
* AWS Console → EC2 → Key Pairs → **Import key pair**
* Paste the public key

### Why import?

* AWS accepts only **key pairs it knows**
* Importing allows using **custom SSH keys**

---

## Step 4 – Create EC2 Instance

* Name: `nautilus-ec2`
* Type: `t2.micro`
* AMI: Amazon Linux / Ubuntu
* Key pair: **imported temp key**
* Security Group:

  * Allow SSH (22)

### Common confusion here

* EC2 **always forces a key pair**
* The task does NOT care about its name
* It is only for **initial access**

---

## Step 5 – SSH into EC2 Using Temporary Key

```bash
ssh -i ~/ec2-temp ec2-user@<EC2-PUBLIC-IP>
```

### Command breakdown

* `ssh` → secure shell
* `-i ~/ec2-temp` → specify private key
* `ec2-user@IP` → default Amazon Linux user

⚠️ Root login is **disabled by default**

---

## Step 6 – Switch to Root User

```bash
sudo -i
```

### Why?

* Task requires adding key to **root**
* `sudo` → run command as admin
* `-i` → start login shell as root

---

## Step 7 – Prepare Root SSH Directory

```bash
mkdir -p /root/.ssh
chmod 700 /root/.ssh
```

### Meaning

* `mkdir -p` → create directory if missing
* `.ssh` → SSH config directory
* `chmod 700` → only root can access it (required by SSH)

---

## Step 8 – Copy Public Key from aws-client

Exit EC2 first:

```bash
exit
exit
```

Confirm you are back on aws-client:

```bash
uname -n
```

Copy public key:

```bash
cat /root/.ssh/id_rsa.pub
```

---

## Step 9 – Paste Public Key into EC2

SSH back into EC2:

```bash
ssh -i ~/ec2-temp ec2-user@<EC2-IP>
sudo -i
```

Edit authorized keys:

```bash
vi /root/.ssh/authorized_keys
```

### Important rule

* **DO NOT delete existing content**
* Add your key on a **new line**

### vi editor actions

* `i` → insert mode
* paste key
* `Esc` → exit insert mode
* `:wq` → save and quit

Fix permissions:

```bash
chmod 600 /root/.ssh/authorized_keys
```

---

## Step 10 – Final Test (MOST IMPORTANT)

Exit EC2:

```bash
exit
exit
```

From aws-client:

```bash
ssh root@<EC2-IP>
```

### Success condition

* Logs in **without password**
* No `.pem` file required
* Passwordless SSH achieved ✅

---

## Mistakes & Confusions Faced (Learning Points)

### ❌ Mistake 1 – Trying to SSH as root initially

* Root login is disabled by default
* Must use `ec2-user` + AWS key first

### ❌ Mistake 2 – Confusion about where commands run

* `cat id_rsa.pub` → **aws-client**
* `authorized_keys` → **EC2**

### ❌ Mistake 3 – Thinking existing authorized_keys must be removed

* Removing it could lock you out
* authorized_keys supports **multiple keys**

---

## Key Takeaways

* AWS key pairs = **bootstrap only**
* SSH keys inside Linux = **real access**
* Public key → server
* Private key → client
* Root access must be explicitly enabled

---

## One-Line Memory Rules

* **Public key goes to server, private key stays on client**
* **Ctrl + D = exit shell**
* **authorized_keys can contain multiple keys**
* **If permissions are wrong, SSH fails**

---

## Final Reflection

This task combined:

* AWS
* Linux
* SSH
* Security best practices

It reflects **real DevOps workflows**, not just console clicking.

```

---

### Final note (important)
Day 22 is a **huge milestone**.  
If you understood *why* this worked — you’ve crossed from **cloud beginner → DevOps-ready**.

When you’re ready, send **Day 23** 🚀
```
