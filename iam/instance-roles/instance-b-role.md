# Instance B IAM Role (Admin Monitoring Server)

Instance B is designated as the administrative monitoring server. A dedicated IAM role is attached to the EC2 instance to define system-level permissions required for monitoring and controlled administrative operations.

This role does not represent human user access and is used exclusively by the EC2 instance.

---

## Role Purpose

The purpose of this IAM role is to:
- Enable AWS Systems Manager (SSM) integration
- Allow controlled execution of approved SSM commands
- Support monitoring and administrative interaction with Instance A

---

## Attached Policies

### AWS Managed Policies
- **AmazonSSMManagedInstanceCore**  
  Enables the EC2 instance to register with AWS Systems Manager and support Session Manager connectivity.

### Customer Inline / Managed Policies
- **ZTA-AdminOps-Monitor-InstanceA**  
  Grants scoped permission to execute approved SSM Run Command actions targeting Instance A only.

The JSON definition for this policy is provided under:

`iam/policies/instance-b/`

---

## Security Considerations

Permissions associated with this role are intentionally scoped and do not grant general EC2, VPC, or IAM administrative access. All administrative interaction is performed through AWS Systems Manager, ensuring auditability and eliminating direct network access to the instance.
