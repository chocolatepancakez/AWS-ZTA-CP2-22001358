# EC2 Admin Role

The EC2 Admin Role is an IAM role intended for authorized administrative users who require elevated privileges to manage and monitor EC2-based resources. This role does not grant standing access and must be explicitly assumed by users when administrative actions are required.

Due to the sensitive nature of the permissions, access through this role is tightly controlled and audited.

---

## Role Purpose

The purpose of this role is to:
- Perform approved EC2 administrative operations
- Support operational management and troubleshooting activities
- Enable administrative access through AWS Systems Manager (SSM) where required

This role is not intended for routine access and is used only when elevated privileges are necessary.

---

## Attached Policies

### Customer Inline / Managed Policies
- **EC2-Admin-Policy**  
  Grants administrative permissions required to manage EC2 resources within the defined project scope.

- **ZTA-Admin-SSM-Policy**  
  Grants permissions to initiate and manage SSM-based access and operations.

- **ZTA-Admin-VPCOps**  
  Grants limited permissions for VPC-related operations required for infrastructure management.

- **ZTA-EC2-AdminSafeOps**  
  Restricts administrative actions to approved and safe EC2 operations.

- **ZTA-Admin-CloudWatchReadOnly**  
  Grants read-only access to CloudWatch logs and metrics for monitoring and troubleshooting purposes.

These policies are modularized to separate responsibilities and reduce the blast radius of administrative access.

---

## Role Assumption Conditions

Access to this role is subject to the following conditions:
- Multi-Factor Authentication (MFA) is mandatory
- Role assumption must be performed explicitly using AWS Security Token Service (STS)
- Permissions are granted only for the duration of the assumed role session

Role assumption permissions are granted via inline policies attached to the corresponding IAM user group.

---

## Security Considerations

Although this role provides elevated privileges, risk is mitigated through:
- Explicit role assumption (no standing admin access)
- MFA enforcement for all role assumptions
- Separation of permissions into scoped, purpose-specific policies
- Centralized logging and audit of administrative actions

This aligns with Zero Trust principles by ensuring that administrative access is deliberate, temporary, and auditable.
