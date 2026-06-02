### Bandit Level 21 → Level 22
Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

Commands you may need to solve this level

cron, crontab, crontab(5) (use “man 5 crontab” to access this)

```bash
bandit21@bandit:~$ crontab -l
crontabs/bandit21/: fopen: Permission denied
bandit21@bandit:~$ ls -l /etc/cron.d
total 40
-r--r----- 1 root root  47 Apr  3 15:18 behemoth4_cleanup
-rw-r--r-- 1 root root 123 Apr  3 15:10 clean_tmp
-rw-r--r-- 1 root root 120 Apr  3 15:17 cronjob_bandit22
-rw-r--r-- 1 root root 122 Apr  3 15:17 cronjob_bandit23
-rw-r--r-- 1 root root 120 Apr  3 15:17 cronjob_bandit24
-rw-r--r-- 1 root root 201 Apr  8  2024 e2scrub_all
-r--r----- 1 root root  48 Apr  3 15:19 leviathan5_cleanup
-rw------- 1 root root 138 Apr  3 15:19 manpage3_resetpw_job
-rwx------ 1 root root  52 Apr  3 15:21 otw-tmp-dir
-rw-r--r-- 1 root root 396 Jan  9  2024 sysstat
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:~$ ls -l /usr/bin/cronjob_bandit22.sh 
-rwxr-x--- 1 bandit22 bandit21 130 Apr  3 15:17 /usr/bin/cronjob_bandit22.sh
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh 
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

# writing bandit22's password to a file in /tmp, and making it readable by everyone (644 permissions)

bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
bandit21@bandit:~$ 
```