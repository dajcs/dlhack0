# Bandit Level 32 → Level 33

Level Goal

After all this git stuff, it’s time for another escape. Good luck!

Commands you may need to solve this level

sh, man

```bash
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0
$ ssh bandit32@bandit.labs.overthewire.org -p 2220
#                          _                     _ _ _
#                         | |__   __ _ _ __   __| (_) |_
#                         | '_ \ / _` | '_ \ / _` | | __|
#                         | |_) | (_| | | | | (_| | | |_
#                         |_.__/ \__,_|_| |_|\__,_|_|\__|
#
#
#                       This is an OverTheWire game server.
#             More information on http://www.overthewire.org/wargames
#
# backend: gibson-1
# bandit32@bandit.labs.overthewire.org's password:
#
#       ,----..            ,----,          .---.
#      /   /   \         ,/   .`|         /. ./|
#     /   .     :      ,`   .'  :     .--'.  ' ;
#    .   /   ;.  \   ;    ;     /    /__./ \ : |
#   .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
#   ;   |  ; \ ; | |    :     | /___/ \ |    ' '
#   |   :  | ; | ' ;    |.';  ; ;   \  \;      :
#   .   |  ' ' ' : `----'  |  |  \   ;  `      |
#   '   ;  \; /  |     '   :  ;   .   \    .\  ;
#    \   \  ',  /      |   |  '    \   \   ' \ |
#     ;   :    /       '   :  |     :   '  |--"
#      \   \ .'        ;   |.'       \   \ ;
#   www. `---` ver     '---' he       '---" ire.org
#
#
# Welcome to OverTheWire!
#
# If you find any problems, please report them to the #wargames channel on
# discord or IRC.
#
# --[ Playing the games ]--
#
#   This machine might hold several wargames.
#   If you are playing "somegame", then:
#
#     * USERNAMES are somegame0, somegame1, ...
#     * Most LEVELS are stored in /somegame/.
#     * PASSWORDS for each level are stored in /etc/somegame_pass/.
#
#   Write-access to homedirectories is disabled. It is advised to create a
#   working directory with a hard-to-guess name in /tmp/.  You can use the
#   command "mktemp -d" in order to generate a random and hard to guess
#   directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
#   restricted so that users cannot snoop on eachother. Files and directories
#   with easily guessable or short names will be periodically deleted! The /tmp
#   directory is regularly wiped.
#   Please play nice:
#
#     * don't leave orphan processes running
#     * don't leave exploit-files laying around
#     * don't annoy other players
#     * don't post passwords or spoilers
#     * again, DONT POST SPOILERS!
#       This includes writeups of your solution on your blog or website!
#
# --[ Tips ]--
#
#   This machine has a 64bit processor and many security-features enabled
#   by default, although ASLR has been switched off.  The following
#   compiler flags might be interesting:
#
#     -m32                    compile for 32bit
#     -fno-stack-protector    disable ProPolice
#     -Wl,-z,norelro          disable relro
#
#   In addition, the execstack tool can be used to flag the stack as
#   executable on ELF binaries.
#
#   Finally, network-access is limited for most levels by a local
#   firewall.
#
# --[ Tools ]--
#
#  For your convenience we have installed a few useful tools which you can find
#  in the following locations:
#
#     * gef (https://github.com/hugsy/gef) in /opt/gef/
#     * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
#     * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
#     * pwntools (https://github.com/Gallopsled/pwntools)
#     * radare2 (http://www.radare.org/)
#
# --[ More information ]--
#
#   For more information regarding individual wargames, visit
#   http://www.overthewire.org/wargames/
#
#   For support, questions or comments, contact us on discord or IRC.
#
#   Enjoy your stay!
#
# WELCOME TO THE UPPERCASE SHELL
>> ls -l
# sh: 1: LS: Permission denied


# The UPPERCASE SHELL is converting every command to uppercase
# since linux commands are lowercase, we get a permission denied error for every command we try to execute.


# except there is one trick:
# $0 converted to uppercase is $0

# Special variables in bash:
# $0   # current shell/script name
# $1   # first argument
# $2   # second argument
# $#   # number of arguments
# $@   # all arguments as separate words
# $$   # PID of current shell

# $0 expands to sh and it is going to execute sh as a command, so we get a "normal" shell
>> $0
$ ls -al
total 36
drwxr-xr-x   2 root     root      4096 Apr  3 15:17 .
drwxr-xr-x 150 root     root      4096 Apr  3 15:20 ..
-rw-r--r--   1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root      3851 Apr  3 15:10 .bashrc
-rw-r--r--   1 root     root       807 Mar 31  2024 .profile
-rwsr-x---   1 bandit33 bandit32 15144 Apr  3 15:17 uppershell

# luckily there is a setuid binary owned by bandit33, so we can get the password for bandit33
$ whoami
bandit33
$ cat /etc/bandit_pass/bandit33
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0

```
