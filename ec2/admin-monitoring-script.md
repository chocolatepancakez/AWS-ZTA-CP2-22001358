# Admin Monitoring Script

This document describes the monitoring script executed on the Admin Monitoring EC2 instance.

The script demonstrates how administrative monitoring tasks are performed using AWS Systems Manager (SSM) without direct network access to target instances.

---

## Purpose

The monitoring script was used to:
- Perform administrative checks on Instance A
- Execute commands remotely using AWS Systems Manager
- Retrieve command output without SSH access
- Log monitoring results locally on the admin instance

---

## Execution Method

- The script is executed on the Admin Monitoring EC2 instance
- Remote commands are sent using `aws ssm send-command`
- The `AWS-RunShellScript` document is used
- Output is retrieved using `get-command-invocation`

All actions are identity-authenticated and logged by AWS.

---

## Monitoring Script

```bash
#!/bin/bash

INSTANCE_A="i-0df614b9ddd0eda63"
TIMESTAMP=$(date +%Y-%m-%d_%H-%M-%S)
OUTFILE="/opt/ops/CollectedLogs/monitor_${TIMESTAMP}.log"

echo "===== Monitoring Instance A =====" >> $OUTFILE
echo "Timestamp: $(date -u)" >> $OUTFILE
echo "" >> $OUTFILE

# Run the stat command remotely on Instance A
COMMAND_ID=$(aws ssm send-command \
  --instance-ids "$INSTANCE_A" \
  --document-name "AWS-RunShellScript" \
  --parameters '{"commands":["stat /opt/hr/hr_confidential_records.txt"]}' \
  --query "Command.CommandId" \
  --output text \
  --region ap-southeast-2)

sleep 1

RAW_OUTPUT=$(aws ssm get-command-invocation \
  --command-id "$COMMAND_ID" \
  --instance-id "$INSTANCE_A" \
  --region ap-southeast-2 \
  --query "StandardOutputContent" \
  --output text)

# Clean the escaped characters (\n, \t, quotes)
CLEAN_OUTPUT=$(printf "%b" "$RAW_OUTPUT")

echo "$CLEAN_OUTPUT" >> $OUTFILE
echo "" >> $OUTFILE
echo "===== END =====" >> $OUTFILE
