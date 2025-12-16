# Instance A IAM Role (HR Confidential Server)

Instance A hosts HR-confidential workloads and operates entirely within private subnets. A dedicated IAM role is attached to the EC2 instance to define the permissions granted to the instance itself.

This role does not represent human access and is not used for administrative interaction.

---

## Role Purpose

The purpose of this IAM role is to:
- Enable integration with AWS Systems Manager (SSM)
- Allow controlled access to approved AWS services
- Support private-only operation without direct internet access

---

## Attached Policies

### AWS Managed Policies
- **AmazonSSMManagedInstanceCore**  
  Enables the EC2 instance to register with AWS Systems Manager and support Session Manager connectivity.

- **AmazonEC2FullAccess**  
  This policy was attached during the implementation phase to support infrastructure setup and testing activities.

### Customer Inline / Managed Policies
- **ZTA-HR-Server-S3ReadOnly**  
  Grants read-only access to approved Amazon S3 resources required for HR-related operations.

The JSON for this policy is provided under:

`iam/policies/instance-a/`

---

## Security Considerations

In the intended Zero Trust security posture, Instance A does not require broad EC2 administrative permissions. The presence of `AmazonEC2FullAccess` is acknowledged as an implementation-phase configuration and is not required for normal operation.

All interactive access to the instance is performed via AWS Systems Manager Session Manager, and no inbound network access is permitted.
