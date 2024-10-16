## BECOMING ROOT WITH SU
pwn.college{QlwXzFcerDNr7fo3au0-C1ympUd.dVTN0UDLykzN0czW}
 ```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{QlwXzFcerDNr7fo3au0-C1ympUd.dVTN0UDLykzN0czW}

```
here i simply got root access using su, then i entered the password as given, then i read the flag

## OTHER USERS WITH SU
pwn.college{UkDHvgGCqFLfJOUti_lF4O7LFAr.dZTN0UDLykzN0czW}

```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{UkDHvgGCqFLfJOUti_lF4O7LFAr.dZTN0UDLykzN0czW}
```
here very similar to the prev one, instead of elevating to the root, i went into a different user, entered the password which was dont-hack-me and then i ran the challenge

## CRACKING PASSWORDS
pwn.college{M686lzixO5RKg4dXt5JJ9jF3UzC.ddTN0UDLykzN0czW}

```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:21 100% 2/3 0.04712g/s 274.4p/s 274.4c/s 274.4C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{M686lzixO5RKg4dXt5JJ9jF3UzC.ddTN0UDLykzN0czW}
```
so here i first used the john the ripper command where we basically do john "file_name"
this gave me the passowrd
so i elevated to the zardus user
entered the password that i found and then ran my challenge

## USING SUDO

Instead of switching to "root," administrators use sudo to temporarily act like "root" and run commands with superpowers.
Instead of needing a special root password, sudo just checks a list of rules (in a file called /etc/sudoers) to decide if the user is allowed to run a command with special permissions.
This makes it easier and more secure, especially when managing lots of computers.
Example of using sudo:

Normally, you can’t read a sensitive file like /etc/shadow because it’s protected.
But if you use sudo, you can run the same command with superuser permissions and read the file.

So basically sudo can give u access to any protected file as long as im allowed to access it ofc

pwn.college{Yug9yACJYYLQKGXRwTuvysQTAuj.dhTN0UDLykzN0czW}

i just did 
```
sudo cat /flag
```


--------------------------
Key Differences:
su: You fully switch to the root user (you have root's full power) and need the root password.
sudo: You stay as yourself but temporarily "borrow" root’s power to run just one command. You don’t need the root password—just your own, if you're allowed to use sudo.
Why people prefer sudo:
Security: You don't have to share the root password.
Control: Admins can control which users can run which commands using sudo (via /etc/sudoers).
