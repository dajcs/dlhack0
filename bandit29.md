# Bandit Level 28 → Level 29

Level Goal

There is a git repository at ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

Commands you may need to solve this level

git

```bash
# cloning the repository on local machine with the correct port 2220 specified
anemet@c2r6s4 ~/goinfre/dlhack0
 % git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
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
# bandit28-git@bandit.labs.overthewire.org's password: 
# remote: Enumerating objects: 9, done.
# remote: Counting objects: 100% (9/9), done.
# remote: Compressing objects: 100% (6/6), done.
# remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
# Receiving objects: 100% (9/9), done.
# Resolving deltas: 100% (2/2), done.
# anemet@c2r6s4 ~/goinfre/dlhack0
 % cd repo
anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % ls -l
# total 4
# -rw-r--r-- 1 anemet 2025_luxembourg 111 Jun  2 14:30 README.md
anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % cat README.md 
# # Bandit Notes
# Some notes for level29 of bandit.

## credentials

# - username: bandit29
# - password: xxxxxxxxxx

anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % git lg            
* adc7f88 (HEAD -> master, origin/master, origin/HEAD) fix info leak
* a3437bd add missing data
* cb630ec initial commit of README.md
anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % git show adc7f88
# commit adc7f885a129baee883058b8a870739489f80194 (HEAD -> master, origin/master, origin/HEAD)
# Author: Morla Porla <morla@overthewire.org>
# Date:   Fri Apr 3 15:17:54 2026 +0000
# 
#     fix info leak
# 
# diff --git a/README.md b/README.md
# index d4e3b74..5c6457b 100644
# --- a/README.md
# +++ b/README.md
# @@ -4,5 +4,5 @@ Some notes for level29 of bandit.
#  ## credentials
#  
#  - username: bandit29
# -- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
# +- password: xxxxxxxxxx
 
 % 


```
