# Creating a Cron Job to Generate Files Every 10 Seconds

## Overview
This guide explains how to create a cron job in Linux that generates a new file every 10 seconds until manually stopped.

## Steps to Implement

### 1. Create a Shell Script
Create a new shell script, e.g., `file_creator.sh`:

```sh
#!/bin/bash
while true; do
    touch "/path/to/directory/file_$(date +%s).txt"
    sleep 10
done
```

This script continuously creates a new file with a timestamped name every 10 seconds.

### 2. Make the Script Executable
Run the following command to give execution permission:

```sh
chmod +x file_creator.sh
```

### 3. Run the Script in the Background
Start the script in the background using:

```sh
nohup ./file_creator.sh > /dev/null 2>&1 &
```

- `nohup` ensures the script runs even after logging out.
- `> /dev/null 2>&1` redirects output and errors to `/dev/null`.
- `&` runs the script in the background.

### 4. Stopping the Script
Find and stop the running script:

```sh
ps aux | grep file_creator.sh
```

Kill the process using:

```sh
kill <PID>
```

Replace `<PID>` with the actual process ID.

## Alternative: Using a Systemd Service
For a more structured approach, create a systemd service instead of running the script in the background.

Let me know if you need further details! 🚀

