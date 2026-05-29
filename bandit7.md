bandit6@bandit:/$ 
bandit6@bandit:/$ find . -group bandit6 -user bandit7 2>/dev/null
./var/lib/dpkg/info/bandit7.password
bandit6@bandit:/$ 

bandit6@bandit:/$ ls -l ./var/lib/dpkg/info/bandit7.password
-rw-r----- 1 bandit7 bandit6 33 Apr  3 15:17 ./var/lib/dpkg/info/bandit7.password
bandit6@bandit:/$ 
bandit6@bandit:/$ cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
bandit6@bandit:/$ 
