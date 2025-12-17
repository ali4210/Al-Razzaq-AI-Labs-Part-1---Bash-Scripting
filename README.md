
# 🐚 Bash Scripting & Linux Automation Portfolio
**Author:** Saleem Ali
**Focus:** Linux Automation, System Administration, & DevOps
**Tech Stack:** Bash, Shell, Cron, Regex, Systemd

---

## 📋 Comprehensive Lab Index
*Click any module to jump to the code.*

| Module | Labs Covered | Key Concepts |
| :--- | :--- | :--- |
| **1. Scripting Basics** | Labs 1–5 | Shebang, Permissions, Variables, Comments |
| **2. Control Flow** | Labs 6–8 | If/Else Conditions, File Tests, Loops |
| **3. System Interaction** | Labs 9–12 | Input (`read`), Arguments (`$1`), Exit Codes |
| **4. Advanced Logic** | Labs 13–15 | Functions, Arrays, Case Statements (Menus) |
| **5. Automation Tools** | Labs 16–20 | Cron Jobs, Backup Scripts, Log Monitoring |
| **6. Text Processing** | Labs 21–25 | Grep, Sed, Awk, Redirection (`>`, `|`) |

---

## 🟢 Module 1: The Foundation

### 🐚 Lab 1: The "Hello World" & Permissions
* **Goal:** Create an executable script.
* **Modern Standard:** Always use `chmod +x` to make it runnable.
```bash
#!/bin/bash

# This is a comment
echo "Hello, System Administrator!"

# To run:
# chmod +x hello.sh
# ./hello.sh

```

### 🐚 Lab 3: Variables & Interpolation

* **Goal:** Store and use data.
* **Best Practice:** Use UPPERCASE for constants, lowercase for local variables.

```bash
#!/bin/bash

USER_NAME="Saleem"
CURRENT_DIR=$(pwd)  # Modern command substitution

echo "User: $USER_NAME is currently in $CURRENT_DIR"

```

---

## 🔵 Module 2: Control Flow (Logic)

### 🔀 Lab 6: Conditionals (If/Else)

* **Goal:** Make decisions based on system state.
* **Modern Syntax:** Use `[[ ... ]]` for robust testing.

```bash
#!/bin/bash

FILE="config.txt"

if [[ -f "$FILE" ]]; then
    echo "$FILE exists."
else
    echo "Error: $FILE not found. Creating it..."
    touch "$FILE"
fi

```

### 🔄 Lab 8: Loops (For & While)

* **Goal:** Automate repetitive tasks.

```bash
#!/bin/bash

# Loop through files
for file in *.log; do
    echo "Processing $file..."
    # mv "$file" "archive/$file" (Example action)
done

# While loop (Server Monitoring)
count=1
while [[ $count -le 5 ]]; do
    echo "Ping Check $count: Server is UP"
    ((count++))
done

```

---

## 🟠 Module 3: System Interaction & Input

### ⌨️ Lab 9: User Input (Read)

* **Goal:** Create interactive scripts.

```bash
#!/bin/bash

read -p "Enter your server IP: " SERVER_IP
read -sp "Enter password: " PASSWORD  # -s hides input
echo
echo "Connecting to $SERVER_IP..."

```

### 🧩 Lab 10: Command Line Arguments

* **Goal:** Pass data to script without interactivity.

```bash
#!/bin/bash

# Usage: ./deploy.sh production
ENV=$1

if [[ -z "$ENV" ]]; then
    echo "Usage: $0 <environment>"
    exit 1
fi

echo "Deploying to $ENV environment..."

```

---

## 🟣 Module 4: Advanced Logic & Functions

### 📦 Lab 13: Functions

* **Goal:** Modularize code (Don't Repeat Yourself).

```bash
#!/bin/bash

check_status() {
    local service=$1
    if systemctl is-active --quiet "$service"; then
        echo "✅ $service is running."
    else
        echo "❌ $service is DOWN."
    fi
}

check_status "nginx"
check_status "docker"

```

### 📋 Lab 15: Case Statements (System Menu)

* **Goal:** Build a CLI tool for admins.

```bash
#!/bin/bash

echo "1. Show Disk Usage"
echo "2. Show Memory Usage"
echo "3. Exit"
read -p "Choose an option: " choice

case $choice in
    1)
        df -h
        ;;
    2)
        free -m
        ;;
    3)
        echo "Goodbye!"
        exit 0
        ;;
    *)
        echo "Invalid Option"
        ;;
esac

```

---

## 🟤 Module 5: Automation & Backups

### 💾 Lab 17: Automated Backup Script

* **Goal:** Compress and archive data with timestamps.

```bash
#!/bin/bash

SOURCE="/var/www/html"
DEST="/backups"
DATE=$(date +%Y-%m-%d_%H%M)
ARCHIVE="backup_$DATE.tar.gz"

echo "Starting backup..."
tar -czf "$DEST/$ARCHIVE" "$SOURCE" 2>/dev/null

if [[ $? -eq 0 ]]; then
    echo "Backup Successful: $ARCHIVE"
else
    echo "Backup Failed!"
fi

```

### ⏰ Lab 20: Cron Automation

* **Goal:** Schedule the backup script.
* **Action:** Edit crontab (`crontab -e`).

```bash
# Run backup every day at 3:00 AM
0 3 * * * /home/user/scripts/backup.sh >> /var/log/backup.log 2>&1

```

---

## 🔴 Module 6: Text Processing (The Power Tools)

### 🔍 Lab 22: Grep, Cut, & Awk

* **Goal:** Extract data from logs.

```bash
#!/bin/bash

LOG_FILE="/var/log/syslog"

echo "Extracting Error messages..."
grep "Error" "$LOG_FILE" > errors.txt

echo "Extracting Usernames from /etc/passwd..."
awk -F: '{print $1}' /etc/passwd

```

---

**Status:** Completed
**Skills:** Shell Scripting, Linux Admin, Cron, Text Processing, System Automation.

```


```
