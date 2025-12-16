# VPC Endpoints Configuration

## Overview
VPC endpoints are configured in this Zero Trust reference model to enable private connectivity between resources within the VPC and required AWS services. This design eliminates the need for public internet access while ensuring that essential management and logging services remain accessible.

## Configured VPC Endpoints
The following VPC endpoints are configured as part of the implementation to support private-only operation of the environment.

| Name          | Endpoint Type | Service Name                                   | Status     |
|---------------|---------------|-----------------------------------------------|------------|
| ssm           | Interface     | com.amazonaws.ap-southeast-2.ssm               | Available  |
| ssm messages  | Interface     | com.amazonaws.ap-southeast-2.ssmmessages       | Available  |
| ec2 messages  | Interface     | com.amazonaws.ap-southeast-2.ec2messages       | Available  |
| s3 gateway    | Gateway       | com.amazonaws.ap-southeast-2.s3                | Available  |

These endpoints allow EC2 instances deployed in private subnets to communicate with AWS services over the AWS internal network.

## Endpoint Types
- **Interface Endpoints**  
  Interface endpoints are used for AWS Systems Manager (SSM), EC2 Messages, and SSM Messages. These endpoints are deployed within the private subnets and provide private IP addresses for secure service communication.

- **Gateway Endpoint**  
  A Gateway VPC endpoint is used for Amazon S3 to allow private access to S3 services without routing traffic through the public internet.

## Purpose and Function
The configured VPC endpoints support the following functions:
- Secure instance access and management via AWS Systems Manager Session Manager
- Delivery of SSM commands and session data
- Access to Amazon S3 for file retrieval
- Operation of EC2 instances without Internet Gateway or NAT Gateway dependency

## Zero Trust Alignment
The use of VPC endpoints strengthens the Zero Trust posture by:
- Preventing direct outbound internet connectivity from EC2 instances
- Ensuring all AWS service communication remains within the AWS private network
- Supporting identity-based access through IAM-controlled AWS services
- Reducing the external attack surface

Network connectivity to AWS services does not imply trust, as all actions are authenticated and authorized using IAM policies.

## Design Considerations
Only the minimum required VPC endpoints are configured to support system functionality. No additional endpoints are enabled, adhering to the principle of least privilege and minimizing unnecessary exposure within the VPC.
