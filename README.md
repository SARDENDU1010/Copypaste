# Copypaste

#!/bin/bash

# Define source and destination directories
SRC_CLIENT="D:/loaniq/client/sdk-core/scbscripts/scriptedAPI"
SRC_SERVER="D:/loaniq/server/scripts/scriptedAPI"

DEST_CLIENT="D:/loaniq/client/sdk-core/scbscripts/scriptedAPI"
DEST_SERVER="D:/loaniq/server/scripts/scriptedAPI"

# Define backup directories
BACKUP_DIR="D:/loaniq/backup_$(date +%Y%m%d_%H%M%S)"
BACKUP_CLIENT="$BACKUP_DIR/client"
BACKUP_SERVER="$BACKUP_DIR/server"

# Create backup directories
mkdir -p "$BACKUP_CLIENT"
mkdir -p "$BACKUP_SERVER"

echo "Backing up current files..."
cp -r "$DEST_CLIENT"/* "$BACKUP_CLIENT"/
cp -r "$DEST_SERVER"/* "$BACKUP_SERVER"/

echo "Replacing with latest files..."
cp -r "$SRC_CLIENT"/* "$DEST_CLIENT"/
cp -r "$SRC_SERVER"/* "$DEST_SERVER"/

echo "Deployment completed successfully."
echo "Backup stored at: $BACKUP_DIR"

# Rollback instructions
echo ""
echo "To rollback, run the following commands:"
echo "cp -r \"$BACKUP_CLIENT\"/* \"$DEST_CLIENT\"/"
echo "cp -r \"$BACKUP_SERVER\"/* \"$DEST_SERVER\"/"
