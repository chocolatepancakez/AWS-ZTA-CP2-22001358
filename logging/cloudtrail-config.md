# AWS CloudTrail Configuration

AWS CloudTrail is used to provide account-level auditing of all AWS API activity. It records actions performed by IAM users, assumed roles, and AWS services.

CloudTrail supports visibility into identity-based actions and is a core component of the system’s monitoring strategy.

---

## Purpose

CloudTrail is used to:
- Log all IAM role assumptions
- Record EC2, VPC, and Systems Manager API calls
- Support investigation of authorized and unauthorized access attempts
- Provide evidence for security validation

---

## Scope of Logging

The following activities are recorded:
- `sts:AssumeRole` events
- IAM authentication and authorization actions
- EC2 management operations
- Systems Manager API calls (e.g., StartSession, SendCommand)

CloudTrail is configured at the account level and applies to all regions.
