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
