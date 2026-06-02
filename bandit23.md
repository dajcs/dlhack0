# Bandit Level 22 → Level 23

Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

Commands you may need to solve this level

cron, crontab, crontab(5) (use “man 5 crontab” to access this)


```bash
bandit22@bandit:~$ ls -l /etc/cron.d
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

# checking the cron jobs, and finding the one for bandit23
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23 
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null

# checking the script for bandit23, and understanding what it does
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget

# when running the script we're running as bandit22
bandit22@bandit:~$ myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
Copying passwordfile /etc/bandit_pass/bandit22 to /tmp/8169b67bd894ddbb4412f91573b38db3

# so when checking tmp files, we can find the password for bandit22 in /tmp/8169b67bd894ddbb4412f91573b38db3 - but we need the password for bandit23
bandit22@bandit:~$ cat /etc/bandit_pass/$myname
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

bandit22@bandit:~$ cat /tmp/8169b67bd894ddbb4412f91573b38db3
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

# if script is run with setuid for bandit23, then the whoami command will return bandit23, and the password for bandit23 will be written to /tmp/8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ myname=bandit23
bandit22@bandit:~$ echo $myname
bandit23
bandit22@bandit:~$ mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
bandit22@bandit:~$ echo $mytarget
8ca319486bfbbc3663ea0fbe81326349

# so we can find the password for bandit23 in /tmp/8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
bandit22@bandit:~$ 
```
