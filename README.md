# AWS Zero Trust Architecture – System Files Submission

This repository contains the system configuration files for the implemented AWS Zero Trust Architecture developed for PRJ3223 Capstone Project 2(CP2).

The contents of this repository serve as supporting technical evidence for the final report and document how identity-based access control, private connectivity, access enforcement, logging, and validation were implemented.

---

## Repository Overview

The repository is structured to reflect the key architectural and security components described in the project methodology and evaluation chapters.

- `architecture/`
- `iam/`
- `ssm/`
- `logging/` 
- `validation/` 

## Folder Descriptions

### Architecture (`/architecture`)
Contains the proposed Zero Trust Architecture reference diagram used in the project.  
The diagram provides a high-level visual overview of the system design, including the private VPC, EC2 instances, IAM roles, AWS Systems Manager access flow, VPC endpoints, and logging components.

---

### Identity and Access Management (`/iam`)
Documents the IAM configuration used in the system, including:
- IAM roles for EC2 instances
- Human access roles (HR, Admin, Read-Only)
- Role assumption model using AWS STS
- MFA enforcement through trust policies
- Customer-managed and inline policy definitions

This folder supports the identity-based access control design described in the report.

---

### Systems Manager (`/ssm`)
Documents the configuration of AWS Systems Manager used as the sole access mechanism for EC2 instances.  
This includes the use of Session Manager to eliminate SSH access and inbound network connectivity, enforcing identity-based access instead of network-based trust.

---

### Logging (`/logging`)
Documents the logging and monitoring mechanisms implemented in the system, including:
- AWS CloudTrail for identity-based API activity
- AWS Systems Manager session logging

These logs provide auditability and support security monitoring and evaluation.

---

### Validation (`/validation`)
Contains validation artefacts aligned with the four evaluation metrics defined in the project:
1. Authorized Session Success Rate  
2. Unauthorized Identity Access Denial Rate  
3. MFA Condition Enforcement Rate  
4. Internet Egress Block Rate  

Each metric is validated through controlled test cases performed on the deployed system.

---

## Notes

- AWS-managed policies are referenced by name and are not included as JSON files.
- All configuration files reflect the final deployed system state.
- This repository is intended for academic submission and review purposes and is not designed as a reusable deployment template.

---

## Report Mapping

This repository directly supports:
- Chapter 3: Methodology  
- Chapter 4: Results and Discussion  

All files align with the system design, implementation, and evaluation presented in the final report.
