##🐧 System Resource Monitor (sys_monitor.sh)

A lightweight Bash script designed for continuous, real-time monitoring of essential system resources (CPU, Memory, Disk) on Linux environments. It sends color-coded alerts when usage exceeds defined thresholds.

##💡 Quick Overview

#Feature

Description

#Purpose

Real-time system monitoring and alerting.

#Environment

Strictly Linux/Unix only (requires top, free, awk, tput).

Alerts

Prints a $\text{RED}$ alert to the console if a threshold is breached.

Refresh

Updates every 2 seconds.

🛠️ Prerequisites and Installation

This script relies on several standard Linux utilities. You must ensure the following packages are installed on your system.

Required Utilities:

procps: Provides the core monitoring commands (top, free).

bc: The arbitrary precision calculator (required for accurate floating-point math if the script is modified).

tput: Used for color output and text formatting in the terminal.

Installation Command Examples:

Distribution

Command

Debian/Ubuntu

sudo apt update && sudo apt install procps bc ncurses-base

RHEL/CentOS

sudo dnf install procps bc ncurses

⚙️ Configuration

The alert sensitivity is controlled by three variables at the top of the script. You can easily adjust these values in sys_monitor.sh:

Variable

Monitored Resource

Default Value

Description

CPU_THRESHOLD

CPU Usage

80

Alert if CPU utilization $\ge 10\%$

MEMORY_THRESHOLD

Memory Usage

80

Alert if Memory utilization $\ge 10\%$

DISK_THRESHOLD

Root Disk (/) Usage

80

Alert if Disk usage percentage $\ge 10\%$

🚀 Execution Guide

1. Download and Save

Save the code into a file named sys_monitor.sh.

2. Grant Permissions

Make the script executable:

chmod +x sys_monitor.sh


3. Run the Monitor

Execute the script from your terminal. It will clear the screen and display real-time updates.

./sys_monitor.sh


4. Stop Monitoring

Press Ctrl + C to gracefully exit the script's infinite loop.

🧩 Troubleshooting and Common Errors

The most common issues relate to inconsistencies in command output across different Linux kernel versions.

Error Message

Cause

Resolution

./sys_monitor.sh: X: command not found

A required utility (bc, top, or free) is missing from the system.

Install the missing package(s) using your distribution's package manager (e.g., apt install procps bc).

Incorrect CPU/Memory calculation (e.g., high numbers)

The field numbers used by awk ($2, $4, etc.) in the top or free commands are incorrect for your Linux distribution's output format.

Modify the awk portion of the script to match the field containing the idle CPU or available memory on your specific system.
