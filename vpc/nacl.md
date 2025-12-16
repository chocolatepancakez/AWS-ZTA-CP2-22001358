# Network Access Control List (NACL) Configuration

## Overview
Network Access Control Lists (NACLs) provide stateless, subnet-level traffic filtering within a VPC. In this Zero Trust reference model, the default NACL configuration is retained and no custom NACL rules are introduced.

## NACL Design Decision
The default NACL is associated with all subnets in the VPC and allows all inbound and outbound traffic. This design choice is intentional and aligns with AWS best practices, where Security Groups are used as the primary mechanism for network access control.

## Justification
Security Groups are stateful and operate at the instance level, making them more suitable for enforcing fine-grained access control and micro-segmentation. In contrast, NACLs are stateless and operate at the subnet level, which can introduce unnecessary complexity when strict instance-level control is already enforced.

By relying on Security Groups as the primary network enforcement layer, the architecture avoids duplicated or conflicting rules while maintaining clarity and manageability.

## Zero Trust Alignment
The use of default NACLs does not weaken the Zero Trust posture of the environment because:
- All inbound traffic to EC2 instances is still restricted by Security Groups
- No Internet Gateway or NAT Gateway is attached to the VPC
- Public subnets are unused for workload deployment
- All access paths are controlled through identity-based mechanisms

This approach ensures that Zero Trust enforcement remains focused on identity verification and least-privilege access rather than redundant network filtering.
