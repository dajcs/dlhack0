# Bandit Level 29 → Level 30

Level Goal

There is a git repository at ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

Commands you may need to solve this level

git

## cloning the repository on local machine with the correct port 2220 specified

```bash
anemet@c2r6s4 ~/goinfre/dlhack0
 % git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
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
# bandit29-git@bandit.labs.overthewire.org's password: 
# remote: Enumerating objects: 16, done.
# remote: Counting objects: 100% (16/16), done.
# remote: Compressing objects: 100% (11/11), done.
# remote: Total 16 (delta 2), reused 0 (delta 0), pack-reused 0
# Receiving objects: 100% (16/16), done.
# Resolving deltas: 100% (2/2), done.
# anemet@c2r6s4 ~/goinfre/dlhack0
 % cd repo
anemet@c2r6s4 ~/goinfre/dlhack0/repo

# checking the contents of the repository, we find a README.md file
 % ls -l
# total 4
# -rw-r--r-- 1 anemet 2025_luxembourg 131 Jun  2 14:53 README.md
anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % cat README.md 
# # Bandit Notes
# Some notes for bandit30 of bandit.
# 
# ## credentials
# 
# - username: bandit30
# - password: <no passwords in production!>

# There is no password in production -- but maybe there is in development?
# Let's check the git log and branches for any clues about the password for bandit30.

anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % git lg
# * 97622e0 (origin/dev, dev) add data needed for development
# * 3e3a2f6 add gif2ascii
# | * b7c20bd (origin/sploits-dev) add some silly exploit, just for shit and giggles
# |/  
# * 921cad1 (HEAD -> master, origin/master, origin/HEAD) fix username
# * edd6383 initial commit of README.md
anemet@c2r6s4 ~/goinfre/dlhack0/repo


# Let's checkout the dev branch

anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % git checkout dev
# Switched to branch 'dev'
# Your branch is up to date with 'origin/dev'.
anemet@c2r6s4 ~/goinfre/dlhack0/repo
 % cat README.md 
# # Bandit Notes
# Some notes for bandit30 of bandit.
# 
# ## credentials
# 
# - username: bandit30
# - password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

```