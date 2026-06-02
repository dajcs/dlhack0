# Bandit Level 25 → Level 26

Level Goal

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.

Commands you may need to solve this level

ssh, cat, more, vi, ls, id, pwd


```bash
# what is in our home dir?
bandit25@bandit:~$ ls -al
total 40
drwxr-xr-x   2 root     root     4096 Apr  3 15:17 .
drwxr-xr-x 150 root     root     4096 Apr  3 15:20 ..
-rw-r-----   1 bandit25 bandit25   33 Apr  3 15:17 .bandit24.password
-r--------   1 bandit25 bandit25 1679 Apr  3 15:17 bandit26.sshkey
-rw-r-----   1 bandit25 bandit25  151 Apr  3 15:17 .banner
-rw-r--r--   1 root     root      220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root     3851 Apr  3 15:10 .bashrc
-rw-r-----   1 bandit25 bandit25   66 Apr  3 15:17 .flag
-rw-r-----   1 bandit25 bandit25    4 Apr  3 15:17 .pin
-rw-r--r--   1 root     root      807 Mar 31  2024 .profile

```

## Trying to login to bandit26 with the ssh key from the 42 host

```bash
# we can't login from localhost so we exit bandit.labs.overthewire.org and try to ssh into bandit26 with the bandit26.sshkey

# but first we need to download the ssh key to our local machine at 42


anemet@c2r6s4 ~/goinfre/dlhack0
 % scp -P 2220 bandit25@bandit.labs.overthewire.org:./bandit26.sshkey .
                         _                     _ _ _   
#                         | |__   __ _ _ __   __| (_) |_ 
#                         | '_ \ / _` | '_ \ / _` | | __|
#                         | |_) | (_| | | | | (_| | | |_ 
#                         |_.__/ \__,_|_| |_|\__,_|_|\__|
#                                                        
# 
#                       This is an OverTheWire game server. 
#             More information on http://www.overthewire.org/wargames
# 
# backend: gibson-0
# bandit25@bandit.labs.overthewire.org's password: 
# bandit26.sshkey                                           100% 1679    61.2KB/s   00:00


# checking bandit26.sshkey permissions are correct for ssh
anemet@c2r6s4 ~/goinfre/dlhack0
 % ls -l bandit26.sshkey 
-r-------- 1 anemet 2025_luxembourg 1679 Jun  2 12:27 bandit26.sshkey

# trying to ssh into bandit26 with the ssh key
# unfortunately we see diplayed the bandit26 banner and then we're getting disconnected immediately after, which means that the shell for bandit26 is not working as expected
anemet@c2r6s4 ~/goinfre/dlhack0
 % ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220

# ...
# ...
# 
#   Enjoy your stay!
# 
#   _                     _ _ _   ___   __  
#  | |                   | (_) | |__ \ / /  
#  | |__   __ _ _ __   __| |_| |_   ) / /_  
#  | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
#  | |_) | (_| | | | | (_| | | |_ / /| (_) |
#  |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/ 
# Connection to bandit.labs.overthewire.org closed.
# anemet@c2r6s4 ~/goinfre/dlhack0
#  % 

```

## Checking the shell for bandit26

```bash

# back on bandit.labs.overthewire.org, we can check the shell for bandit26 in /etc/passwd
bandit25@bandit:~$ cat /etc/passwd | grep bandit2[4-6]
bandit24:x:11024:11024:bandit level 24:/home/bandit24:/bin/bash
bandit25:x:11025:11025:bandit level 25:/home/bandit25:/bin/bash
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext

# checking the contents of /usr/bin/showtext, which is the shell for bandit26
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
bandit25@bandit:~$ 
```


## Tricking the shell for bandit26 to get a real shell


Shrink your terminal window to just a few lines tall before connecting, so `text.txt` overflows the screen and `more` is forced to paginate. 

Once paused in `more`, we have an escape: `more` (backed by `vi` for this) lets us press `v` to open the file in `vi`.
Now inside `vi` command mode (entered by pressing `:`), we can set the `shell` environmental variable and launch it:

```vi
:set shell=/bin/bash
:shell
```


```bash

anemet@c2r6s4 ~/goinfre/dlhack0
 % ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _   
#                         | |__   __ _ _ __   __| (_) |_ 
#                         | '_ \ / _` | '_ \ / _` | | __|
#                         | |_) | (_| | | | | (_| | | |_ 
#                         |_.__/ \__,_|_| |_|\__,_|_|\__|
#                                                        
#    ...
# 
#  | |                   | (_) | |__ \ / /  
#  | |__   __ _ _ __   __| |_| |_   ) / /_  
#  | '_ \ / _` | '_ \ / _` | | __| / / '_ \
#  | |_) | (_| | | | | (_| | | |_ / /| (_) |
# --More--(77%)

# pressing 'v' to open the file in vi
# v
# pressing ':' to enter command mode in vi
# :set shell=/bin/bash
# :shell
bandit26@bandit:~$ ls -al
total 44
drwxr-xr-x   3 root     root      4096 Apr  3 15:17 .
drwxr-xr-x 150 root     root      4096 Apr  3 15:20 ..
-rwsr-x---   1 bandit27 bandit26 14888 Apr  3 15:17 bandit27-do
-rw-r--r--   1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root      3851 Apr  3 15:10 .bashrc
-rw-r--r--   1 root     root       807 Mar 31  2024 .profile
drwxr-xr-x   2 root     root      4096 Apr  3 15:17 .ssh
-rw-r-----   1 bandit26 bandit26   258 Apr  3 15:17 text.txt
bandit26@bandit:~$ ls -l /etc/bandit_pass/bandit26
-r-------- 1 bandit26 bandit26 33 Apr  3 15:17 /etc/bandit_pass/bandit26

# getting the password for bandit26 (just for fun, since we already have a shell as bandit26)
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ

```