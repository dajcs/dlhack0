
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think
Commands you may need to solve this level

ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)


bandit20@bandit:~$ ls -al
total 36
drwxr-xr-x   2 root     root      4096 Apr  3 15:17 .
drwxr-xr-x 150 root     root      4096 Apr  3 15:20 ..
-rw-r--r--   1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root      3851 Apr  3 15:10 .bashrc
-rw-r--r--   1 root     root       807 Mar 31  2024 .profile
-rwsr-x---   1 bandit21 bandit20 15612 Apr  3 15:17 suconnect
bandit20@bandit:~$ 