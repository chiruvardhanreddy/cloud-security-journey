# Day 3: Processes, services and log filtering

## What I learned
- A process is a running program. Each one has a PID (a number).
- ps aux lists all running processes. top shows them live (q to quit).
- sleep 300 & runs a program in the background. kill PID stops it.
- df -h shows disk space. free -h shows memory. uname -a shows system info.
- systemctl lists services (background programs). console-getty is a normal login service.
- A full disk can stop logging, which is a security problem.

## Text tools
- grep word file: shows only lines containing the word.
- grep -c counts matching lines. grep -v shows lines that do NOT match.
- head -n shows the first lines. tail -n shows the last lines.
- wc -l counts lines in a file.
- A pipe | sends the output of one command into the next.
- sort puts lines in order. uniq -c collapses repeats and counts them. It needs sort first.
- awk '{print $NF}' prints the last word of each line.

## Lab: find the attacker IP
Command: grep "Failed" auth.log | awk '{print $NF}' | sort | uniq -c | sort -nr
Result: 203.0.113.5 had the most failed logins (3). This looks like a brute-force attempt.

## Lesson
Small commands chained with pipes are how I find suspicious activity in logs.
