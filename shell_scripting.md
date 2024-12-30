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