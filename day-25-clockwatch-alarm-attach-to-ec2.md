# Day 25 – CloudWatch Alarm for EC2 CPU

## What I did
- Launched an EC2 instance named `nautilus-ec2` using Ubuntu AMI
- Created a CloudWatch alarm `nautilus-alarm`
- Monitored EC2 CPU utilization
- Configured alarm to trigger when CPU >= 90% for 5 minutes
- Set SNS topic `nautilus-sns-topic` for notifications

## What I learned
- CloudWatch monitors AWS resource metrics
- Alarms are created based on metric thresholds
- SNS is used to send notifications when alarms trigger

## About SNS (Simple Notification Service):
An Amazon SNS (Simple Notification Service) topic is a 
logical access point and communication channel used in a 
publish/subscribe (pub/sub) messaging paradigm. Publishers 
send messages to a topic, and Amazon SNS then efficiently delivers 
these messages to all subscribed endpoints, which can be a variety of 
application-to-application (A2A) or application-to-person (A2P) destinations. 

## One-line takeaway
> CloudWatch alarms help detect performance issues and notify teams automatically.

## Proof of work:
<img width="1919" height="935" alt="Screenshot 2026-01-20 190351" src="https://github.com/user-attachments/assets/2588dc43-7b07-468b-81a0-11f4c32ce617" />
