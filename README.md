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
````
## STEP 1: Explore the Linux Authentication Log
**Log File:**
- On most Linux systems, the main authentication log file is:
   - **Debian/Ubuntu:** /var/log/auth.log
   - **CentOS/RHEL/Fedora:** /var/log/secure
- This log contains authentication events like:
   - SSH logins
   - ``sudo`` usage
   - User login attempts (successful and failed)
   - PAM (Pluggable Authentication Module) events
## 📚 Author
![AWS](https://img.shields.io/badge/Built%20by-juniorkalomba-orange?style=flat&logo=amazonaws) 
**🔗 Feel free to contribute or suggest improvements!** 
<p align="right">
  <a href="https://www.linkedin.com/in/junior-kalomba-10002a18a/" target="_blank">
    <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="junior-kalomba-10002a18a" height="30" width="40"/>  
   

