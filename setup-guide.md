# Setup Guide: Cloud Threat Detection Lab

This guide provides step-by-step instructions to set up a cloud monitoring and threat detection lab using AWS Free Tier services.

## 1. Launch EC2 Instance

1. Navigate to the AWS Management Console and open EC2.
2. Click Launch instance.
3. Configure the instance:
   - Name: security-lab-instance
   - AMI: Amazon Linux 2 (Free Tier eligible)
   - Instance type: t3.micro
4. Create or select an existing key pair for SSH access.
5. Configure Security Group:
   - Allow SSH (port 22) from your IP address
6. Click Launch instance.
7. Verify that the instance state is Running.

## 2. Enable AWS CloudTrail

1. Navigate to the AWS Management Console and open CloudTrail.
2. Click Create trail
3. Configure the trail with the following settings:
   - Trail Name: `security-lab-trail`
   - Apply trail to all regions: Enabled
   - Storage location: Create a new S3 bucket
   - Log file validation: Enabled
4. Review the configuration and click Create trail.

## 3. Configure CloudWatch Monitoring

### Basic Monitoring

1. Navigate to EC2 and select instance.
2. Open the Monitoring tab.
3. Verify that metrics such as:
   - CPU Utilization
   - Network In/Out are being collected.

## 4. Create CloudWatch Alarm

1. Navigate to CloudWatch.
2. Click Alarms → Create alarm.
3. Select metric:
   - EC2 → Per-Instance Metrics → CPU Utilization
4. Configure threshold:
   - Threshold type: Static
   - Condition: CPU Utilization > 70%
5. Configure notification:
   - Create an SNS topic
   - Added email subscription
6. Provide a name (security-alerts)
7. Click Create alarm.

## 5. Simulate Attack Scenarios

Perform the following attack simulations:

### 5.1 Failed SSH Login Attempts

- Execute multiple SSH login attempts using an invalid user:
  ssh fakeuser@<your-ec2-ip>

### 5.2 Port Scanning (Reconnaissance)

- Perform a port scan using Nmap:
  sudo nmap -sS -Pn <your-ec2-ip>

### 5.3 Suspicious IAM Activity

- Create and delete IAM users
- Attach administrative policies for testing purposes

## 6. Analyze Logs

- Navigate to CloudTrail → Event history.
- Use Lookup attributes to filter logs by:
        CreateUser
        DeleteUser
        ConsoleLogin
3. Review event details such as timestamp, user identity, and event source.

## 7. Capture Screenshots

Capture and store the following screenshots:
- EC2 instance running state
- CloudTrail trail configuration
- CloudWatch metrics (CPU/Network)
- CPU spike (if simulated)
- SSH failed login attempts (terminal)
- Nmap port scan results
- CloudTrail logs (IAM activity)

Store all screenshots in the /screenshots directory.

## 8. Create Architecture Diagram

- Use a diagram tool such as draw.io.
- Include the following components:
      EC2 instance
      CloudTrail
      S3 bucket
      CloudWatch
Export as architecture-diagram.png.

## Completion
You have successfully set up a cloud-based threat detection lab using AWS monitoring and logging services.