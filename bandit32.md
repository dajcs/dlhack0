# Bandit Level 31 → Level 32

Level Goal

There is a git repository at ssh://bandit31-git@bandit.labs.overthewire.org/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

Commands you may need to solve this level

git


```bash
$ git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
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
# bandit31-git@bandit.labs.overthewire.org's password:
# remote: Enumerating objects: 4, done.
# remote: Counting objects: 100% (4/4), done.
# remote: Compressing objects: 100% (3/3), done.
# remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
# Receiving objects: 100% (4/4), done.
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0
$ cd repo
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ ls -al
total 0
drwxrwxrwx 1 neat neat 4096 Jun  2 20:54 .
drwxrwxrwx 1 neat neat 4096 Jun  2 20:54 ..
drwxrwxrwx 1 neat neat 4096 Jun  2 20:54 .git
-rwxrwxrwx 1 neat neat    6 Jun  2 20:54 .gitignore
-rwxrwxrwx 1 neat neat  147 Jun  2 20:54 README.md
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
# checking the .gitignore file, we see that .txt files are ignored by git
$ cat .gitignore
*.txt
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo

# checking the README.md file, we find a hint about pushing a file key.txt to the repository
$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

# making sure we are on the master branch
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git lg
* 1b45e2d (HEAD -> master, origin/master, origin/HEAD) initial commit

# creating the key.txt file
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ echo 'May I come in?' > key.txt
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ cat key.txt
May I come in?

# checking the status of the repository, we see that key.txt is an untracked file
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

# using the -f flag to force git to add the key.txt file - this adds the file despite the fact that it is ignored by the .gitignore file
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git add -f key.txt
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   key.txt

# committing the key.txt file to the repository
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git commit -m "Add key.txt"
[master 86e5e18] Add key.txt
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt

# pushing the new commit to the remote repository
# this will trigger a pre-receive hook on the server that will check the key.txt
# and return the password for the next level if the key.txt is found and contents is correct
neat@dellw:/mnt/c/Users/dajcs/code/dlhack0/repo
$ git push
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
# bandit31-git@bandit.labs.overthewire.org's password:
# Permission denied, please try again.
# bandit31-git@bandit.labs.overthewire.org's password:
# Enumerating objects: 4, done.
# Counting objects: 100% (4/4), done.
# Delta compression using up to 20 threads
# Compressing objects: 100% (2/2), done.
# Writing objects: 100% (3/3), 328 bytes | 36.00 KiB/s, done.
# Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
# remote: ### Attempting to validate files... ####
# remote:
# remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
# remote:
# remote: Well done! Here is the password for the next level:
# remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K

```
