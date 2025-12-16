# Security Group Configuration

## Overview
Security Groups (SGs) are used as the primary network-level enforcement mechanism in this Zero Trust reference model. They provide instance-level, stateful filtering to control inbound and outbound traffic within the VPC. All rules are explicitly defined to suppo rtsegmentation and least-privilege network access.

## Security Group Design
A single Security Group is applied to both EC2 instances in this implementation. Network access is restricted to explicitly permitted internal traffic and controlled service communication.

### Inbound Rules
| Rule | Protocol | Port Range | Source | Description |
|-----|---------|------------|--------|-------------|
| 1 | TCP | 0–65535 | Self (same SG) | Allow internal communication only between instances associated with the same Security Group |
| 2 | TCP | 443 | 10.1.0.0/16 | Allow HTTPS traffic originating from within the VPC |

### Outbound Rules
| Rule | Protocol | Port Range | Destination | Description |
|-----|---------|------------|-------------|-------------|
| 1 | All | All | 0.0.0.0/0 | Allow outbound traffic (no Internet Gateway or NAT Gateway present) |

## Micro-Segmentation Enforcement
The self-referencing inbound rule ensures that only instances explicitly assigned to the same Security Group can communicate with each other. This design restricts east-west traffic and reduces the risk of lateral movement in the event of a compromised resource.

Any instance not associated with this Security Group is unable to initiate communication with protected resources, enforcing identity-based segmentation at the network layer.

## Zero Trust Alignment
The Security Group configuration supports Zero Trust principles by:
- Denying all inbound traffic by default unless explicitly allowed
- Restricting communication to known and authorized internal sources
- Eliminating implicit trust based on subnet placement or IP address
- Supporting least-privilege network access

Network-level access alone does not grant resource access. All instance access is further gated by AWS Identity and Access Management (IAM) and AWS Systems Manager Session Manager (SSM), ensuring that network permissions do not equate to user trust.

## Design Considerations
Although outbound traffic is allowed at the Security Group level, the absence of an Internet Gateway or NAT Gateway ensures that no external connectivity is possible. This separation of logical permission and physical reachability simplifies rule management while maintaining strict network isolation.
