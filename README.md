# AWS-ZTA-CP2-22001358

This repository contains the system files and configuration artefacts for the Capstone Project 2 titled:

**Zero Trust Architecture in AWS: Theory vs Practical Enforcement**

The project implements a fully private Zero Trust reference model in AWS using native services only, focusing on practical enforcement of identity-based segmentation and least-privilege access.

---

## Project Scope
- Fully private AWS VPC (no Internet Gateway or NAT Gateway)
- Identity-based access using AWS IAM roles and policies
- AWS Systems Manager Session Manager (SSM) as the only access path
- VPC Endpoints and AWS PrivateLink for private connectivity
- Continuous logging via AWS CloudTrail and SSM Session Logs

---

## Repository Structure
- `architecture/` – Reference model and network diagrams
- `iam/` – IAM users, groups, roles, trust and permission policies
- `vpc/` – VPC design, Security Groups, NACL, and VPC endpoint configurations
- `ssm/` – Session Manager configuration and logging setup

---

## Notes
This repository is created for academic submission purposes only.  
No AWS credentials, access keys, or sensitive identifiers are included.
