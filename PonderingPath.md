## THE PATH VARIABLE
pwn.college{s2mJbgjBWIoUfwK_R0WqZsZMrYf.dZzNwUDLykzN0czW}

i interrupted the process of /challenge/run which was trying to delete my flag using path
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{s2mJbgjBWIoUfwK_R0WqZsZMrYf.dZzNwUDLykzN0czW}
```

## SETTING PATH
pwn.college{8tk1KHXL0cBCjlcFjBEMs0xKGKM.dVzNyUDLykzN0czW}
so i was told to get a flag "win" must be invoked which is done using /challenge/run but that is stored in the directory /challenge/more_commands
so with the guidance of the example give i did
```
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{8tk1KHXL0cBCjlcFjBEMs0xKGKM.dVzNyUDLykzN0czW}
```

## ADDING COMMANDS
pwn.college{k6umg60pEGCgpVcrqQYg2yajvUO.dZzNyUDLykzN0czW}

this one was very hard and time-consuming so I had to note down the steps:

find location of cat for which I learnt about the which command:
```
hacker@path~adding-commands:~$ which cat
/run/workspace/bin/cat
make win script such that it cats the flag using location of cat
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ chmod ugo+x win
```
in the win script, my code was: /bin/cat /flag. initially I tried /run/workspace/bin/cat but it was not working.

add the win script to PATH without overwriting PATH. for this I learnt that appending :$PATH adds the directory to PATH without removing its previous directories.
```
hacker@path~adding-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~adding-commands:~$ echo $PATH
/home/hacker:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```
running /challenge/run
```
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
```

## HIJACKING COMMANDS
pwn.college{YMYmIG9ResQrubnVgnkwKSNbkEu.ddzNyUDLykzN0czW}

for this task I figured I'd have to make my own rm command so that when the PATH variable is searched, it uses the directory in which my command lies, instead of the original one.
first I created the rm command:
```

hacker@path~hijacking-commands:~$ touch rm
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ chmod ugo+x rm
```
i made the script of rm to be: echo you have disabled rm!; /bin/cat /flag then, like the previous challenge, I added the ~ directory to PATH and ran /challenge/run
```
hacker@path~hijacking-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
you have disabled rm!
```
