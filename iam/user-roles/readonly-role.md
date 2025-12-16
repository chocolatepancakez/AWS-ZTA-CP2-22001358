# Read-Only Access Role

The Read-Only Access Role is an IAM role intended for users who require visibility into AWS resources without the ability to modify or administer them. This role is designed for auditing, monitoring, and review purposes.

Access through this role does not grant any write or administrative permissions.

---

## Role Purpose

The purpose of this role is to:
- Provide read-only visibility into EC2 and related resources
- Allow users to inspect system state without making changes
- Support review and audit activities

This role is not intended for operational or administrative use.

---

## Attached Policies

### Customer Inline / Managed Policies
- **EC2-ReadOnlyPolicy**  
  Grants read-only access to EC2 resources.

- **SSM-ReadOnlyPolicy**  
  Grants read-only visibility into AWS Systems Manager resources.

These policies ensure users can view system information without the ability to initiate sessions or modify configurations.

---

## Role Assumption Conditions

Access to this role is subject to the following conditions:
- Multi-Factor Authentication (MFA) is required
- Role assumption must be performed explicitly using AWS Security Token Service (STS)

Role assumption permissions are granted via inline policies attached to the corresponding IAM user group.

---

## Security Considerations

This role enforces least privilege by:
- Preventing modification of AWS resources
- Eliminating administrative or operational capabilities
- Requiring explicit role assumption with MFA

Read-only access is logged and supports Zero Trust principles by ensuring visibility without trust-based access.
