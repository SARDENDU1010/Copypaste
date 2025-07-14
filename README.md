#!/bin/bash

# Define source directory for latest JARs
SRC_DIR="D:/51889-loaniq-sdk-ant"

# Define target directories
SERVER_DIR="D:/LoanIQ/server/sdk-post"
CLIENT_DIR="D:/LoanIQ/client/sdk-post"

# Define backup directory with timestamp
BACKUP_DIR="D:/LoanIQ/backup_sdk_$(date +%Y%m%d_%H%M%S)"
BACKUP_SERVER="$BACKUP_DIR/server"
BACKUP_CLIENT="$BACKUP_DIR/client"

# Create backup directories
mkdir -p "$BACKUP_SERVER"
mkdir -p "$BACKUP_CLIENT"

echo "Backing up existing JAR files..."
cp "$SERVER_DIR"/liq-sdk-scripted-api-ant*.jar "$BACKUP_SERVER"/
cp "$CLIENT_DIR"/liq-sdk-scripted-api-ant*.jar "$BACKUP_CLIENT"/

echo "Deploying latest JAR files..."
cp "$SRC_DIR"/liq-sdk-scripted-api-ant*.jar "$SERVER_DIR"/
cp "$SRC_DIR"/liq-sdk-scripted-api-ant*.jar "$CLIENT_DIR"/

echo "Deployment completed successfully."
echo "Backup stored at: $BACKUP_DIR"

# Rollback instructions
echo ""
echo "To rollback, run the following commands:"
echo "cp \"$BACKUP_SERVER\"/liq-sdk-scripted-api-ant*.jar \"$SERVER_DIR\"/"
echo "cp \"$BACKUP_CLIENT\"/liq-sdk-scripted-api-ant*.jar \"$CLIENT_DIR\"/"

# One-time change note
echo ""
echo "NOTE: One-time change applied to '51889-loaniq-sdk-generic' (scripted-api folder)."
echo "No further action required for subsequent releases."
