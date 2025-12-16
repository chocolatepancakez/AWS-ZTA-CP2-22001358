# VPC Configuration

## Overview
A Virtual Private Cloud (VPC) was created to host the Zero Trust reference model for this project. The VPC is designed to support strict network isolation and identity-based access control by eliminating all public network exposure and relying on AWS services for secure access.

## VPC Design
- VPC CIDR block: 10.1.0.0/16
- Subnets:
  - Two private subnets hosting EC2 instances
  - Public subnets exist but are not used in this implementation
- Availability zones: Two availability zones for fault isolation and resilience

No EC2 instances or workloads are deployed in public subnets.

## Network Isolation
To enforce Zero Trust principles, the VPC does not include:
- Internet Gateway (IGW)
- NAT Gateway
- Public IP addressing for EC2 instances

Although public subnets exist within the VPC, they remain unused and have no routing paths to the internet. This ensures that all compute resources operate in a fully private network environment.

## Zero Trust Alignment
The private-only operational design of the VPC supports the Zero Trust principle of “never trust, always verify” by:
- Eliminating implicit trust based on network location
- Reducing the external attack surface
- Preventing direct inbound and outbound internet connectivity

All administrative and user access to EC2 instances is performed through AWS Systems Manager Session Manager (SSM), ensuring identity-based authentication, authorization, and full session logging.

## Private Access to AWS Services
To maintain full network isolation while allowing required AWS service communication, VPC endpoints are configured for services such as:
- AWS Systems Manager (SSM)
- EC2 Messages
- SSM Messages
- Amazon S3 (Gateway Endpoint)

These endpoints enable private connectivity over the AWS internal network without exposing resources to the public internet.
