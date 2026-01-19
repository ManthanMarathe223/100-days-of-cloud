# Day 24 – Application Load Balancer

## What I did
- Created an Application Load Balancer `xfusion-alb`
- Created a target group `xfusion-tg`
- Created a security group `xfusion-sg` to allow HTTP traffic
- Attached the security group to the ALB
- Routed traffic from ALB port 80 to EC2 port 80
- Updated EC2 security group to allow traffic from ALB

## What I learned
- ALB distributes traffic to backend instances
- Target groups define where ALB sends traffic
- Security groups control traffic flow at each level
- EC2 must explicitly allow traffic coming from ALB

## One-line takeaway
> Load balancers sit in front of servers and forward traffic securely using target groups.

---
## What i actually did:

- **Security Group (`xfusion-sg`)**
We created a security group that **allows HTTP traffic on port 80 from the public**.
This means **only HTTP requests are allowed to reach the ALB**.

- **Target Group (`xfusion-tg`)**
We created a target group and **registered the EC2 instance** in it.
This tells the **ALB where to forward traffic**.

- **Application Load Balancer (`xfusion-alb`)**
We created an ALB that:

* Listens on **HTTP port 80**
* Uses the **security group** to accept traffic
* Uses the **target group** to forward traffic to EC2 on port 80

- **EC2 Security Group Update**
We updated the EC2 security group to **allow HTTP traffic coming from the ALB security group**.
This allows **ALB → EC2 communication**.

---

> **Security Group controls access, Target Group defines targets, ALB distributes traffic.**

## ALB Architecture Diagram

Internet Users
      |
      v
[ HTTP : 80 ]
      |
      v
+---------------------------+
| Security Group            |
| (xfusion-sg)              |
| Allows HTTP : 80          |
+---------------------------+
              |
              v
+---------------------------+     +-------------------+     +---------------------------+
| Application Load Balancer | --> | Target Group      | --> | Security Group            |
| (xfusion-alb)             |     | (xfusion-tg)      |     | (EC2 Default SG)          |
|                            |     |                   |     | Allows HTTP from ALB SG   |
+---------------------------+     +-------------------+     +---------------------------+
                                                            |
                                                            v
                                                +---------------------------+
                                                | EC2 Instance              |
                                                | (xfusion-ec2)             |
                                                | Nginx on port 80          |
                                                +---------------------------+
