# S3 Bucket Artefacts

This folder contains representative artefacts used to demonstrate secure, identity-based access to Amazon S3 in the Zero Trust Architecture implementation.

---

## Stored Artefact

**File:** `hr_confidential_records.txt`  
**Classification:** HR Confidential (Demonstration File)

The file represents sensitive HR records and is used to validate access control enforcement and monitoring within the system.

---

## Access Model

- The artefact is stored in an Amazon S3 bucket
- Access is restricted using IAM role-based permissions
- EC2 instances access the bucket via an S3 VPC gateway endpoint
- No public access or internet connectivity is permitted

---

## Usage in System

- Instance A (HR Confidential EC2) retrieves or hosts the artefact
- The Admin Monitoring instance verifies access and file metadata using AWS Systems Manager
- The file is referenced during validation and monitoring activities

---

## Notes

This file is a simulated artefact created solely for academic demonstration purposes.

No real employee data is stored or processed.
