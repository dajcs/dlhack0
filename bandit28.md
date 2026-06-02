# Bandit Level 27 → Level 28

Level Goal

There is a git repository at ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

Commands you may need to solve this level

git


## 1st try to clone the repository on local machine

Fails because we are trying to clone the repository on port 22 instead of 2220, which is the port for the bandit wargames.

```bash
anemet@c2r6s4 ~/goinfre/dlhack0
 % git clone ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo
# Cloning into 'repo'...
# The authenticity of host 'bandit.labs.overthewire.org (13.63.65.121)' can't be established.
# ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
# This host key is known by the following other names/addresses:
#     ~/.ssh/known_hosts:13: [hashed name]
# Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
# Warning: Permanently added 'bandit.labs.overthewire.org' (ED25519) to the list of known hosts.
# 
#                       This is an OverTheWire game server. 
#             More information on http://www.overthewire.org/wargames
# 
# !!! You are trying to log into this SSH server on port 22, which is not intended.
# !!! If you are trying to log in to an OverTheWire game, use the port mentioned in
# !!! the "SSH Information" on that game's webpage (in the top left corner).
# 
# bandit27-git@bandit.labs.overthewire.org: Permission denied (publickey).
# fatal: Could not read from remote repository.
# 
# Please make sure you have the correct access rights
# and the repository exists.
anemet@c2r6s4 ~/goinfre/dlhack0
```

## The trick: specifying the port with `:2220` after the hostname

```bash
anemet@c2r6s4 ~/goinfre/dlhack0
 % git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo

# Cloning into 'repo'...
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
# backend: gibson-0
# bandit27-git@bandit.labs.overthewire.org's password: 
# remote: Enumerating objects: 3, done.
# remote: Counting objects: 100% (3/3), done.
# remote: Compressing objects: 100% (2/2), done.
# remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
# Receiving objects: 100% (3/3), done.
anemet@c2r6s4 ~/goinfre/dlhack0
 % cd repo
anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % ls -al
total 16
drwxr-xr-x 3 anemet 2025_luxembourg 4096 Jun  2 14:19 .
drwxr-xr-x 4 anemet 2025_luxembourg 4096 Jun  2 14:19 ..
drwxr-xr-x 8 anemet 2025_luxembourg 4096 Jun  2 14:19 .git
-rw-r--r-- 1 anemet 2025_luxembourg   68 Jun  2 14:19 README

# next level password is in README
anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % cat README 
# The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN

```