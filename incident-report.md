# Incident Report: Cloud Threat Detection Lab

## Summary
This report summarizes findings from simulated attack scenarios performed on an AWS EC2 instance.
Monitoring was performed using CloudWatch for EC2 metrics and SNS alerts were configured specifically for CPU utilization spikes.

## Incident 1: Failed SSH Login Attempts (Simulated Attack)

### Observation
- Multiple failed SSH login attempts were intentionally performed as part of the lab
- These attempts resulted in repeated "Permission denied" responses.

### Evidence
- Terminal output showing multiple failed SSH login attempts.
- CloudWatch metrics indicating minor fluctuations in CPU utilization.

### Analysis
- SSH brute-force attempts occur at the operating system level and are not recorded in CloudTrail.
- While repeated login attempts may slightly increase CPU usage, they are not a reliable detection method on their own.
- Detection of such attacks requires system-level logging (e.g., authentication logs within the EC2 instance).

### Recommendation
- Use key-based authentication and disable password-based login.
- Restrict SSH access to trusted IP addresses.
- Monitor system authentication logs (e.g., /var/log/auth.log or /var/log/secure).
- Implement intrusion prevention tools such as Fail2Ban.

## Incident 2: Port Scanning Activity (Reconnaissance)

### Observation
A port scan was performed using Nmap against the EC2 instance.

### Evidence
- Nmap scan results showing only port 22 (SSH) open.
- All other ports were filtered.

### Analysis
- This indicates a minimal attack surface, which is a strong security practice.
- Port scanning is commonly used by attackers to identify exposed services.

### Recommendation
- Maintain minimal open ports in security groups.
- Regularly audit security group rules.
- Monitor unusual network traffic patterns.

## Incident 3: Suspicious IAM Activity

### Observation
- IAM users were created and deleted as part of the simulation.
- Administrative policies were attached during testing.

### Evidence
- CloudTrail logs showing:
    CreateUser
    DeleteUser
    AttachUserPolicy
- Event details include timestamps, user identity, and source.

### Analysis
- These actions represent potential insider threats or compromised credentials.
- IAM activity is critical to monitor, as it directly affects account security.

### Recommendation
- Enable continuous monitoring of IAM activity using CloudTrail.
- Apply the principle of least privilege.
- Set up alerts for sensitive API actions.

## General System Monitoring

### Observation
- EC2 metrics such as CPU utilization and network activity were monitored using CloudWatch.

### Evidence
- CloudWatch metrics dashboards

### Analysis
- CloudWatch provides visibility into system performance and anomalies.
- Metric-based alerts can help identify unusual behavior but should be combined with log analysis.

### Recommendation
- Configure CloudWatch alarms for critical metrics.
- Integrate monitoring with alerting systems (SNS).
- Combine metric monitoring with CloudTrail logs for comprehensive detection.

## Conclusion
The lab demonstrates how to simulate and analyze cloud-based threats using AWS-native tools. While CloudTrail effectively logs API-level activity such as IAM changes, system-level attacks like SSH brute-force attempts require additional logging mechanisms for detection.
