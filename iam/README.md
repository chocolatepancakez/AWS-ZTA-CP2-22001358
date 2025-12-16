# IAM Configuration Overview

This folder contains the Identity and Access Management (IAM) configuration used in the system implementation. IAM is used to enforce identity-based access control and eliminate implicit trust.

Access in this system is structured around:
- IAM roles instead of direct user permissions
- Explicit role assumption using AWS Security Token Service (STS)
- Separation between human access roles and EC2 instance roles
- Multi-Factor Authentication (MFA) enforcement for privileged access

Users do not receive direct permissions to AWS resources. Instead, users are grouped by function and must explicitly assume authorized roles to perform actions.

EC2 instances are also associated with dedicated IAM roles that define what the instance itself is permitted to do.

Detailed role definitions, role-assumption mechanisms, and custom policy artefacts are documented in the files within this folder.
