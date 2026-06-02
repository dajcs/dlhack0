# Bandit Level 30 → Level 31

Level Goal

There is a git repository at ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

Commands you may need to solve this level

git


```bash
$ git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
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
# backend: gibson-1
# bandit30-git@bandit.labs.overthewire.org's password:
# remote: Enumerating objects: 4, done.
# remote: Counting objects: 100% (4/4), done.
# remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
# Receiving objects: 100% (4/4), done.
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0
$ cd repo
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git lg
* e761c5d (HEAD -> master, origin/master, origin/HEAD) initial commit of README.md
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ cat README.md
just an epmty file... muahaha

# checking for tags in the repository
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git tag
secret
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo

# checking the contents of the secret tag, we find the password for bandit31
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy

```
