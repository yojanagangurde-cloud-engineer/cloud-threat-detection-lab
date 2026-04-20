# Attack Scenarios

## 1. SSH Brute-Force Simulation

Command used:
ssh fakeuser@<ec2-public-IPV4>
Multiple failed login attempts were generated

Result: "Permission denied"

### Observation
These attempts are NOT logged in CloudTrail because they occur at the EC2 operating system level.

## 2. Port Scanning

Command used:
sudo nmap -sS -Pn <ec2-public-IPV4>

Result:
- Only port 22 (SSH) open
- All other ports filtered

### Observation:
This indicates a secure configuration with minimal attack surface.

## 3. Suspicious IAM/API Activity

Actions performed:
- Created IAM users
- Deleted users
- Attached admin policies

### Observation:
These actions were successfully logged in CloudTrail and can be used to detect suspicious behavior.

## Key Takeaways
- CloudTrail logs AWS API activity
- Network-level attacks require different monitoring tools
- IAM activity is critical for security detection