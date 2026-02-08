# linux-bash-scripts-or-personal-clould-tab-

#! /bin/bash
# simple backup script - - copies files from one folder to another and logs the backup

# 1. set your source folder (the files you want to back up
SOURCE="$HOME/backup_test"

# 2. set your destination folder (where backups will go)
DEST="$HOME/backup_folder"

# 3. get the current date and time for versioning
DATE=$(date +%Y-%m-%d-%H%M)

if [ ! -d "$SOURCE" ]; then
   echo "Source folder does not exist!"
   echo "Creating source folder for you..."
   mkdir -p "$SOURCE"
   echo "Test file 1" > "$Source/file.txt"
   echo "Test file 2" > "$SOURCE/file2.txt"
fi

# 4. make sure the destination folder exists
mkdir -p "$DEST/backup-$DATE"

# 5 copy all files from source to destination with the date in the folder name
cp -r "$SOURCE/"* "$DEST/backup-$DATE/"

# 6 log the backup in a text file
echo "Backup completed at $DATE" >> "$DEST/backup_log.txt"

# 7 optional: print a message to the terminal
echo "Backup done! Check $DEST for files."
