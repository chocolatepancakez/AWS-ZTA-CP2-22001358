# AWS Systems Manager Session Logging

AWS Systems Manager (SSM) Session Manager is the sole mechanism used for interactive access to EC2 instances in this system.

Session logging is enabled to provide visibility into instance access without relying on SSH or inbound network connectivity.

---

## Purpose

SSM session logging is used to:
- Record all interactive access to EC2 instances
- Associate access events with assumed IAM roles
- Eliminate the need for SSH key-based access
- Support forensic review of access sessions

---

## Logged Information

The following information is recorded for each session:
- Session start and end time
- IAM role and user account used to initiate the session
- Target EC2 instance

Session logs provide evidence that access to instances is controlled and traceable.

---

## Security Benefits

Using SSM Session Manager with logging provides:
- No open inbound ports on EC2 instances
- No SSH key distribution or management
- Centralized access control via IAM
- Full visibility of access events

This supports Zero Trust principles by ensuring all access is explicitly authorized and logged.
