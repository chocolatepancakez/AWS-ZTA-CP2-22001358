# EC2 User Data Script

This document describes the user data script used during the launch of EC2 instances in the Zero Trust Architecture.

The user data script is executed once at instance launch and is responsible for preparing the instance for secure, identity-based access via AWS Systems Manager (SSM).

---

## Purpose

The user data script was used to:
- Install and configure the Amazon SSM Agent
- Force SSM communication through a private VPC interface endpoint
- Enable Systems Manager access without internet connectivity
- Eliminate the need for SSH-based access

---

## User Data Script

```bash
#!/bin/bash

# Install SSM Agent
sudo yum install -y amazon-ssm-agent

# Configure SSM Agent
# Install SSM agent
sudo yum install -y amazon-ssm-agent

# Configure SSM agent
sudo tee /etc/amazon/ssm/amazon-ssm-agent.json > /dev/null <<EOF
{
    "agent": {
        "region": "ap-southeast-2",
        "privateEndpoint": "vpce-0a4f5601ca4ce938e"
    }
}
EOF

# Start SSM agent
sudo systemctl start amazon-ssm-agent
