##  CHANGING FILE OWNERSHIP

pwn.college{4sK-vGRQk2wOHaEhIj_0-C-rSfS.dFTM2QDLykzN0czW}

Here I first changed the ownership of the flag file from the root to the user. Then I tried doing /flag which did not work.   
Then in accordance to the example i did ls -l, which gave a huge list of options. I went thru the list and i tried to run each file and 
eventually got the flag.
```
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
```

## FUN WITH GROUP NAMES

pwn.college{YDIK6yGcOwEY9pFYAcBfGbf8xIb.dJzNyUDLykzN0czW}

This was like the last one too, excpet i was not told which group contains the flag.     I had to use the id command to find the group names, chgrp to that group then i had to list all the files in that grp to cat the file which i thought might contain the flag

```
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
```

## CHANGING PERMISSIONS
pwn.college{AV0d9Ygn_eY8_lVO5ruPq0HLPRd.dNzNyUDLykzN0czW}
```
> chmod o+r /flag
> cat /flag
```
So first i changed the access to all users (including us, the hacker) using chmod o+r. Now that i have acces the /flag, i can use cat /flag to read the file.

## EXECUTABLE FILES

pwn.college{ksoTljiF7qY72HwRNVUroMv9Z69.dJTM2QDLykzN0czW}

So here i needed execution access to /challenge/run. I took a little help from chatgpt here 
```
> chmod u+x /challenge/run
> ls -l /challenge/run
> /challenge/run
```
I obtained user access, listed the props of the challenge, ran it

## Permission tweaking practices
 ```
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod go-r /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw--w----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+w /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": rw--w----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw--w--w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+w /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": rw--w--w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rw--w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+r /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": rw-rw--w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w--w--w-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ug-r /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": -w--w--w-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-rw--w-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+r /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": -w-rw--w-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-rw-rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+r /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": -w-rw-rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---r--r--
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ugo-w /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod /flag
chmod: missing operand after ‘/flag’
Try 'chmod --help' for more information.
hacker@permissions~permission-tweaking-practice:~$ chmod /flag+r
chmod: missing operand after ‘/flag+r’
Try 'chmod --help' for more information.
hacker@permissions~permission-tweaking-practice:~$ chmod ugo+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{03qskTQnmjWPog-PjY4Yv9ANtVq.dBTM2QDLykzN0czW}
```

## PERMISSIONS SETTING PRACTICE 
```
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-rwx-wx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rwx,o=wx /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": -w-rwx-wx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wx-wx-wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=wx,o=wx /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": -wx-wx-wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w--w-r--
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=w,o=r /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": -w--w-r--
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrwx-wx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=rwx,o=wx /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": rwxrwx-wx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw--w--w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=w,o=w /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": rw--w--w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --x-w-r--
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=w,o=r /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": --x-w-r--
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw---x-w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=x,o=w /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": rw---x-w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxr--rwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=r,o=rwx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod /flag=rwx
chmod: missing operand after ‘/flag=rwx’
Try 'chmod --help' for more information.
hacker@permissions~permissions-setting-practice:~$ chmod ugo+r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{EWZxwScwXBkE3OFY6DBK6bKf5yX.dNTM5QDLykzN0czW}

```

## THE SUID BIT
pwn.college{o1-2d1f48H95Q_5pF1RTmPJzKtA.dNTM2QDLykzN0czW}

```
hacker@permissions~the-suid-bit:~$ ls -l /challenge/getroot
-rwsr-xr-x 1 root root 155 Jul 12 10:30 /challenge/getroot
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{o1-2d1f48H95Q_5pF1RTmPJzKtA.dNTM2QDLykzN0czW}
```
first i used ls to see whats happening in /challenge/getroot
then i changed permissions as given in example to u+s
then i ran the challenge
i was given permission
then i read the flag

