# IAM Role Assumption Model

This system implements identity-based access control using explicit IAM role assumption. No IAM users are granted direct permissions to AWS resources. All access is mediated through IAM roles and AWS Security Token Service (STS).

This approach enforces Zero Trust principles by ensuring that access is granted only after explicit authentication, authorization, and validation.

---

## Design Overview

Access control is structured as follows:
- IAM users are placed into functional user groups
- User groups do not grant direct access to AWS resources
- User groups contain inline policies that allow `sts:AssumeRole`
- IAM roles define the actual permissions to AWS resources
- Role assumption requires Multi-Factor Authentication (MFA)

This ensures there are no standing privileges and all privileged access is temporary.

---

## User Groups and Role Mapping

The following IAM user groups are defined:

| User Group       | Assumable IAM Role                   |
|------------------|--------------------------------------|
| ZTA-EC2-Admins   | EC2-Admin-Role                       |
| ZTA-EC2-HR       | ZTA-HR-ConfidentialAccess-Role       |
| ZTA-ReadOnly     | ZTA-ReadOnly-Role                    |

Each user group contains an inline policy that permits role assumption for the mapped role only.

---

## Inline Role Assumption Policies

Inline policies attached to each user group explicitly allow the `sts:AssumeRole` action. These policies are scoped to a single role and include conditional enforcement.

The following security conditions are applied:
- `aws:MultiFactorAuthPresent` must be `true`
- `aws:MultiFactorAuthAge` must be less than or equal to 3600 seconds

This ensures that role assumption is only possible after recent MFA authentication.

---

## Security Properties

This role assumption model provides the following security guarantees:
- No direct user permissions to AWS resources
- Explicit elevation of privilege through role assumption
- MFA enforcement for all privileged roles
- Reduced blast radius through role-specific permissions
- Clear separation between authentication (users) and authorization (roles)

---

## Related Artefacts

The JSON for inline role assumption policies are provided under:

`iam/policies/assume-role`

These files serve as implementation evidence for the access control model described in this file.

