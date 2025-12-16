# HR Confidential Access Role

The HR Confidential Access Role is an IAM role intended for human users who require controlled access to HR-related resources. This role does not grant standing privileges and must be explicitly assumed by authorized users.

Access through this role is restricted and audited to protect sensitive data.

---

## Role Purpose

The purpose of this role is to:
- Allow authorized HR users to access HR-confidential resources
- Enable Systems Manager (SSM) session access where required
- Prevent direct access to infrastructure or administrative operations

---

## Attached Policies

### Customer Inline / Managed Policies
- **ZTA-HR-EC2Describe-Policy**  
  Grants read-only visibility into specific EC2 resources required for contextual awareness.

- **ZTA-HR-SSM-Access-Policy**  
  Grants permission to initiate SSM sessions against approved EC2 instances.

These policies are scoped to HR-related access requirements and do not grant infrastructure modification privileges.

---

## Role Assumption Conditions

This role can only be assumed under the following conditions:
- Multi-Factor Authentication (MFA) is required
- Role assumption is performed explicitly using AWS Security Token Service (STS)

Role assumption permissions are granted via inline policies attached to the corresponding IAM user group.

---

## Security Considerations

This role enforces least-privilege access by:
- Restricting permissions to HR-specific use cases
- Preventing administrative access to EC2, VPC, or IAM resources
- Requiring explicit role assumption with MFA

All access through this role is subject to logging mechanisms configured at the AWS account level.
