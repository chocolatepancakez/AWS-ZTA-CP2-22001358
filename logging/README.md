# Logging and Monitoring Overview

This folder documents the logging and monitoring mechanisms implemented in the system to support visibility and security validation.

Logging is used to:
- Record all identity-based actions performed in the AWS environment
- Track access to EC2 instances via AWS Systems Manager (SSM)
- Support post-access review and security analysis
- Validate Zero Trust enforcement through logging evidence

The primary logging mechanisms used are AWS CloudTrail and AWS Systems Manager session logging.
