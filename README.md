# Cloud Threat Detection Lab

## Overview
This project demonstrates a cloud security monitoring setup on AWS using native services to detect and analyze suspicious activities.

The lab simulates real-world attack scenarios such as:
- Failed SSH login attempts
- Port scanning (reconnaissance)
- Suspicious IAM activity

It uses:
- AWS CloudTrail for API activity logging
- Amazon CloudWatch for monitoring metrics
- Amazon EC2 as a test environment
- Amazon S3 for log storage
- Amazon SNS for alerts

## Objectives
- Monitor AWS API activity and EC2 metrics
- Simulate common attack behaviors
- Analyze logs to identify suspicious patterns
- Document findings like a real-world security analyst

## Architecture
- EC2 instance (test target)
- CloudTrail logging to S3
- CloudWatch metrics + alarms
- SNS for alerting

## Security Features
- Restricted SSH access (only my IP)
- Minimal open ports (only port 22)
- Activity logging with CloudTrail
- Monitoring with CloudWatch metrics and alarms

## Attack Simulations
- Failed SSH login attempts
- Port scanning (reconnaissance)
- Suspicious IAM/API activity

## Key Findings
- SSH attempts are not logged in CloudTrail (OS-level activity)
- CloudTrail effectively logs IAM and API activity
- CloudWatch detects system-level anomalies like CPU spikes

## Screenshots

## EC2 Instance
![ec2](screenshots/ec2-instance.png)

## EC2 Monitoring
![ec2](screenshots/ec2-monitoring.png)

## CloudWatch Metrics
![cloudwatch](screenshots/cloudwatch-metrics.png)

## CloudWatch Alarm
![cloudwatch-alarm](screenshots/cloudwatch-alarm.png)

## SNS Notifications
![sns](screenshots/SNS-Notifications.png)

## CloudTrail Trail Setup
![cloudtrail](screenshots/cloudtrail-trail-setup.png)

## CloudTrail Event History
![cloudtrail-logs](screenshots/cloudtrail-event-history.png)

## SSH Failed Logins
![ssh](screenshots/ssh-failed-logins.png)

## Port Scan
![Port-scan](screenshots/port-scan.png)

## Suspicious API Activity
![api](screenshots/suspicious-api.png)

## S3 Logs
![s3-logs](screenshots/s3-logs.png)

## Architecture Diagram
![architecture](architecture-diagram.png)

## Note on GuardDuty
GuardDuty integration was planned, but due to account subscription restrictions, this project demonstrates manual threat detection using CloudTrail and CloudWatch.

## Skills Demonstrated
- Cloud security monitoring
- AWS logging and auditing
- Threat simulation and analysis
- Incident reporting

## Outcome
This lab simulates how a security analyst detects threats using native AWS tools without relying on automated services like GuardDuty.
