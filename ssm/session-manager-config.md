# AWS Systems Manager Session Manager Configuration

## Purpose
This file documents the configuration used to enable AWS Systems Manager (SSM) Session Manager as the only operational access mechanism to EC2 instances in this project.

Direct network-based access methods such as SSH are intentionally made non-operational to enforce identity-based access control.

## Access Method
All access to EC2 instances is performed using AWS Systems Manager Session Manager. EC2 instances are deployed in private subnets with no public IP addresses, and no inbound access is permitted at the network level.

The access flow is as follows:
1. A user authenticates to AWS using IAM credentials with Multi-Factor Authentication (MFA)
2. The user assumes an authorized IAM role
3. AWS Systems Manager establishes a secure session to the target EC2 instance
4. Session access events are logged

## EC2 Instance Configuration
The following configurations are applied on all EC2 instances:
- SSM Agent is installed and running
- EC2 instances are deployed in private subnets
- No inbound Security Group rules allow SSH (port 22)
- EC2 instances do not have public IP addresses
- An SSH key pair is associated at launch due to AWS requirements; however, SSH-based access is not enabled or used after deployment

These controls ensure that all operational access is performed exclusively through SSM.

## EC2 Instance IAM Role
Each EC2 instance is associated with an IAM role that enables integration with AWS Systems Manager.

### Attached Policy
- **AmazonSSMManagedInstanceCore** (AWS managed)

This policy allows the EC2 instance to register with AWS Systems Manager, maintain secure control and data channels, and support Session Manager connectivity without requiring inbound network access.

## Logging Scope
SSM Session Manager records session access metadata, including:
- Session initiation and termination events
- Target EC2 instance identifiers
- IAM identity and assumed role context

Command-level or keystroke activity within the session is not recorded.

## Security Intent
This configuration enforces the following security properties:
- No direct network access to EC2 instances
- Identity-based access enforcement through IAM
- Explicit session establishment via AWS-managed control planes
- Auditable session access without reliance on SSH or key-based login
