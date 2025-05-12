# 🔍 Log File Analysis with Linux Tools

This project demonstrates basic cybersecurity analysis techniques by examining Linux system authentication logs using powerful command-line tools. The goal is to identify suspicious login behavior, failed SSH login attempts, and potential brute-force attacks.

## Project Overview

- **Objective**: Analyze `/var/log/auth.log` to detect failed login attempts, successful root logins, and brute force patterns.
- **Tools Used**: 
  - `grep`
  - `awk`
  - `cut`
  - `sort`
  - `uniq`
  - `less`, `cat`, `tail`

## 🛠️ What You'll Learn

- How to navigate and read Linux system logs.
- How to use command-line tools for filtering and parsing log data.
- How to detect failed and successful login attempts.
- How to identify brute-force attack patterns.
- How to generate a basic incident report from log findings.

## Files

- `auth_report.txt` – Summary report of findings including IPs with failed logins and successful root access.
- `commands.sh` – (Optional) Bash script version of the analysis for automation.
- `sample_auth.log` – (Optional) Sample log file for practice if you're not using a live system.

## Example Commands

```bash
# View failed SSH login attempts
grep "Failed password" /var/log/auth.log

# Count failed attempts by IP
grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr

# Find successful root logins
grep "Accepted password for root" /var/log/auth.log

# Detect brute-force attempts (IPs with more than 5 failures)
grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | awk '$1 > 5'


