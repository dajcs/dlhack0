# Bandit Level 26 → Level 27

Level Goal

Good job getting a shell! Now hurry and grab the password for bandit27!

Commands you may need to solve this level

ls





```bash

# in bandit26's home dir, we can see a file called bandit27-do with setuid permissions for bandit27

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
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
bandit26@bandit:~$ 
bandit26@bandit:~$ ./bandit27-do 
Run a command as another user.
  Example: ./bandit27-do id
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB


```