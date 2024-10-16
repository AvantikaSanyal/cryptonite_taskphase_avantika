##  CHANGING FILE OWNERSHIP

pwn.college{4sK-vGRQk2wOHaEhIj_0-C-rSfS.dFTM2QDLykzN0czW}

Here I first changed the ownership of the flag file from the root to the user. Then I tried doing /flag which did not work.   
Then in accordance to the example i did ls -l, which gave a huge list of options. I went thru the list and i tried to run each file and 
eventually got the flag.

>  chown hacker /flag
 /flag
ssh-entrypoint: /flag: Permission denied
 chown hacker /flag
 ls -l
total 40
-rw-r--r-- 1 hacker hacker    4 Oct  7 14:51 COLLEGE
drwxr-xr-x 2 hacker hacker 4096 Oct  2 07:33 Desktop
-rw-r--r-- 1 root   hacker    2 Oct  8 16:45 MPF3bojF
-rw-r--r-- 1 hacker hacker    8 Oct  8 04:55 PWN
-rw-r--r-- 1 root   hacker   58 Oct  5 05:19 a
-rw-r--r-- 1 hacker hacker  829 Oct  8 04:37 instructions
-rw-r--r-- 1 root   hacker   77 Oct  8 12:31 intercepted_data
-rw-r--r-- 1 hacker hacker   93 Oct  8 04:37 myflag
lrwxrwxrwx 1 hacker hacker    5 Oct  6 14:48 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker    0 Oct  8 16:36 pwn
-rw-r--r-- 1 root   hacker   77 Oct  8 16:46 pwn_output
-rw-r--r-- 1 hacker hacker    0 Oct  7 15:00 stdout
-rw-r--r-- 1 hacker hacker    0 Oct  7 15:00 stdoyut
-rw-r--r-- 1 hacker hacker  435 Oct  7 15:04 the-flag
hacker@permissions~changing-file-ownership:~$ cat not-the-flag
pwn.college{4sK-vGRQk2wOHaEhIj_0-C-rSfS.dFTM2QDLykzN0czW} 

## GROUPS AND FILES

pwn.college{wHTt1VUEZQzEr0ghCfM8Umlqfe0.dFzNyUDLykzN0czW}

This was similarly related to the first one. All I did was change the grp to the hacker then ls -l to list all the files under it and then i cat that file where i thought the flag might be hidden.

## FUN WITH GROUP NAMES

pwn.college{YDIK6yGcOwEY9pFYAcBfGbf8xIb.dJzNyUDLykzN0czW}

This was like the last one too, excpet i was not told which group contains the flag. I had to use the id command to find the group names, chgrp to that group then i had to list all the files in that grp to cat the file which i thought might contain the flag

>  chgrp grp7547 /flag
   ls -l
total 40
-rw-r--r-- 1 hacker grp7547    4 Oct  7 14:51 COLLEGE
drwxr-xr-x 2 hacker grp7547 4096 Oct  2 07:33 Desktop
-rw-r--r-- 1 root   grp7547    2 Oct  8 16:45 MPF3bojF
-rw-r--r-- 1 hacker grp7547    8 Oct  8 04:55 PWN
-rw-r--r-- 1 root   grp7547   58 Oct  5 05:19 a
-rw-r--r-- 1 hacker grp7547  829 Oct  8 04:37 instructions
-rw-r--r-- 1 root   grp7547   77 Oct  8 12:31 intercepted_data
-rw-r--r-- 1 hacker grp7547   93 Oct  8 04:37 myflag
lrwxrwxrwx 1 hacker grp7547    5 Oct  6 14:48 not-the-flag -> /flag
-rw-r--r-- 1 root   grp7547    0 Oct  8 16:36 pwn
-rw-r--r-- 1 root   grp7547   77 Oct  8 16:46 pwn_output
-rw-r--r-- 1 hacker grp7547    0 Oct  7 15:00 stdout
-rw-r--r-- 1 hacker grp7547    0 Oct  7 15:00 stdoyut
-rw-r--r-- 1 hacker grp7547  435 Oct  7 15:04 the-flag
hacker@permissions~fun-with-groups-names:~$ cat not-the-flag
pwn.college{YDIK6yGcOwEY9pFYAcBfGbf8xIb.dJzNyUDLykzN0czW}

## CHANGING PERMISSIONS
pwn.college{AV0d9Ygn_eY8_lVO5ruPq0HLPRd.dNzNyUDLykzN0czW}

> chmod o+r /flag
> cat /flag

So first i changed the access to all users (including us, the hacker) using chmod o+r. Now that i have acces the /flag, i can use cat /flag to read the file.


