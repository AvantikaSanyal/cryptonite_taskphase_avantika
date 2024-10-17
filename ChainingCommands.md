## CHAINING WITH SEMI COLONS

   ### Semi colon
   used to separate commands in the same line which would otherwise be put into multiple lines
   
pwn.college{8lgUKbhLe0LxHhlgJfpT_zztfDb.dVTN4QDLykzN0czW}

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
```
chained the pwn challenge with college challenhe using semi colon

## YOUR FIRST SHELL SCRIPTS
had to take some help from a friend for this 

pwn.college{oLfz3OUIM8JwYOy6la4ywvsF26v.dFzN4QDLykzN0czW}

first i create the file
```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ ls
COLLEGE  MPF3bojF  a             intercepted_data  not-the-flag  pwn_output  stdoyut   x.sh
Desktop  PWN       instructions  myflag            pwn           stdout      the-flag
```
then i change permission
```
hacker@chaining~your-first-shell-script:~$ ls -l x.sh
-rw-r--r-- 1 hacker hacker 0 Oct 17 09:40 x.sh
hacker@chaining~your-first-shell-script:~$ chmod ugo+x x.sh
hacker@chaining~your-first-shell-script:~$ ls -l x.sh
-rwxr-xr-x 1 hacker hacker 0 Oct 17 09:40 x.sh
```
then i open editor using
```
nano x.sh
```
here i save  my pwn and college challenges
i save the name as x.sh using ctrl+o, exit using ctrl+x

then i use 
```
bash x.sh
```
and get my flag

```
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{oLfz3OUIM8JwYOy6la4ywvsF26v.dFzN4QDLykzN0czW}
```

## REDIRECTING SCRIPT OUTPUT
we need to pipe the script's output to /challenge/solve
pwn.college{UY8dYl2wyHO1AO9y_mYxXCcCzic.dhTM5QDLykzN0czW}

so simply
```
bash x.sh | /challenge/solve
```

## EXECUTABLE SHELL SCRIPTS
pwn.college{cdPrO9mxyf3WhrL4j_OzBPhKIsv.dRzNyUDLykzN0czW}

```
hacker@chaining~executable-shell-scripts:~$ touch script.sh
hacker@chaining~executable-shell-scripts:~$ nanp script.sh
ssh-entrypoint: nanp: command not found
hacker@chaining~executable-shell-scripts:~$ nano script.sh
hacker@chaining~executable-shell-scripts:~$ chmod ugo+x script.sh
hacker@chaining~executable-shell-scripts:~$ ~/script.sh
You must make a shellscript in your home directory that will launch
/challenge/solve, make it executable, and invoke it without explicitly
specifying 'bash'!
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{cdPrO9mxyf3WhrL4j_OzBPhKIsv.dRzNyUDLykzN0czW}
````
i made a script with script.sh, used nano to open the editor and store /challenge/solve in it
then i changed execution permission in it
then i launched it using the command as given


