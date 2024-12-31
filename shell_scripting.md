# Shell Scripting

## Backup Script: Automate the Process of Creating Backups of Important Files or Directories with Timestamped Names

```bash
#!/bin/bash

# Configuration
SOURCE_DIR="/home/ubuntu"       # Directory to backup
BACKUP_DIR="/opt/backup"       # Directory where backups will be stored
LOG_FILE="/opt/backup.log"

# Adding the timestamp
TIMESTAMP=$(date +"%Y-%m-%d:%H-%M")
# Create backup filename with timestamp
BACKUP_FILE="backup_${TIMESTAMP}.tar.gz"

# Ensure the backup directory exists
mkdir -p "$BACKUP_DIR"

if tar -czf "${BACKUP_DIR}/${BACKUP_FILE}" "${SOURCE_DIR}"; then
        echo "[$(date +"%Y-%m-%d:%H-%M")] backup successful:$BACKUP_FILE" | tee -a "$LOG_FILE"
else
        echo "[$(date +"%Y-%m-%d:%H-%M")] Backup failed" | tee -a "$LOG_FILE"
        exit 1
fi

# Optional: Cleanup old backups (e.g., older than 30 days)
find "$BACKUP_DIR" -type f -name "backup_*.tar.gz" -mtime +30 -exec rm -f {} \;

exit 0
```

## shell script to create a VM on aws 
```
#!/bin/bash
# Variables
AMI_ID="ami-0e2c8caa4b6378d8c" # Ubuntu Server 20.04 LTS (HVM), SSD Volume Type
INSTANCE_TYPE="t2.micro"
KEY_NAME="windows"
SECURITY_GROUP="default"

# Tags
TAGS="ResourceType=instance,Tags=[{Key=Name,Value=MyInstance},{Key=Environment,Value=Development}]"

# Create a script to update the Ubuntu machine
USER_DATA=$(cat <<EOF
#!/bin/bash
sudo apt-get update -y
sudo apt-get upgrade -y
EOF
)

# Run the instance with user data and tags
INSTANCE_ID=$(aws ec2 run-instances \
    --image-id $AMI_ID \
    --instance-type $INSTANCE_TYPE \
    --key-name $KEY_NAME \
    --security-group-ids $SECURITY_GROUP \
    --user-data "$USER_DATA" \
    --tag-specifications "$TAGS" \
    --query 'Instances[0].InstanceId' \
    --output text)

echo "Created instance with ID: $INSTANCE_ID with user data to update and upgrade"

# Wait until the instance is running
# aws ec2 wait instance-running --instance-ids $INSTANCE_ID

# Get the public DNS of the instance
PUBLIC_DNS=$(aws ec2 describe-instances --instance-ids $INSTANCE_ID --query 'Reservations[0].Instances[0].PublicDnsName' --output text)

echo "Instance public DNS: $PUBLIC_DNS"
```


