## LEVEL 0

I needed to login to the game like we used to do for pwn college. I used the command:
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
and then i entered 'yes' as it asked, after which it asked me the pw which is "bandit0"

## LEVEL 0 TO LEVEL 1

I logged into my bandit server using:
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
Now I was logged in, and neaded to read a "readme" file that had my password.
so I used 
```
ls
```
This read out the files that I had.
Then i used the following to read the password
```
cat readme
```
Thus I got my password: "ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If"
Next I tried to enter the password, it didn't work, so I asked ChatGPT FOR HELP and i got this :
"Since you are logged into the Bandit server, you won't have permission to create or modify files there. Instead, you need to manage your notes locally,
on your own machine"

Now I used
```
exit
```
This made me go out of my bandit server
Now I had to create a local file to store my password as asked so I did( again with GPT help sorry)
```
echo "Level 1 password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If" >> ~/bandit_notes.txt
```
so now i had appended my password to the file in the home page called bandit_notes.txt
then Ilogged  into my account again
```
ssh bandit1@bandit.labs.overthewire.org -p 2220
```
and finally entered my password again.

## LEVEL 1 TO LEVEL 2
This was similar to the first
i used "ls" to show me what files are there
then i wanted to read the "-" file but that could be taken as a command so i did
```
cat ./-
```
This displayed the password for Level 2: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx.
then i exitted as the previous challenge. 
then in the local file i added the password
```
Level 2 password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx" >> ~/bandit_notes.txt
```
and then i entered the bandit server again
```
bandit2@bandit.labs.overthewire.org -p 2220
```
then it asked me to enter the password and i did and yeah i was logged in

## LEVEL 2 TO LEVEL 3
This was like the last two
So I used "ls" to lis out my files.
it gave me a file called "spaces in this filename"
i did
```
cat spaces in this filename
```
and it did not recognise this as a valid command
so i had to do
```
cat "spaces in this filename
```
this gave me the password for level 3: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
then i logged out of the bandit server
then i had to store this password in the local file
```
"Level 3 password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx" >> ~/bandit_notes.txt
```
logged into the server
```
ssh bandit3@bandit.labs.overthewire.org -p 2220
```
entered the password and i was in

## LEVEL 3 TO LEVEL 4
Here I needed to login again.
This time it said that the password is stored in a hidden file in a directory called inhere
So I needed to move into the directory using
```
cd inhere
```
then i wanted to see hidden files so i did
```
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
```
Now it was obivous where the flag was so I did
```
bandit3@bandit:~/inhere$ cat ./...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
YAY I GOT THE PASSWORD
so again i exited the server
i added the new and most recent password onto my local file with
```
"Level 4 password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ" >> ~/bandit_notes.txt
```
then i logged into the server using my ssh command
I entered my password and VOILA, I was in :)

## LEVEL 4 TO LEVEL 5
```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cat inhere
cat: inhere: Is a directory
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ ls -a
.  ..  -file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ file *
file: Cannot open `ile00' (No such file or directory)
file: Cannot open `ile01' (No such file or directory)
file: Cannot open `ile02' (No such file or directory)
file: Cannot open `ile03' (No such file or directory)
file: Cannot open `ile04' (No such file or directory)
file: Cannot open `ile05' (No such file or directory)
file: Cannot open `ile06' (No such file or directory)
file: Cannot open `ile07' (No such file or directory)
file: Cannot open `ile08' (No such file or directory)
file: Cannot open `ile09' (No such file or directory)
bandit4@bandit:~/inhere$ file --*
file: unrecognized option '--*'
Usage: file [-bcCdEhikLlNnprsSvzZ0] [--apple] [--extension] [--mime-encoding]
            [--mime-type] [-e <testname>] [-F <separator>]  [-f <namefile>]
            [-m <magicfiles>] [-P <parameter=value>] [--exclude-quiet]
            <file> ...
       file -C [-m <magicfiles>]
       file [--help]
bandit4@bandit:~/inhere$ file ./-file00 ./-file01 ./-file02 ./-file03 ./-file04 ./-file05 ./-file06 ./-file07 ./-file08 ./-file09
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat "ASCII text"
cat: 'ASCII text': No such file or directory
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
bandit4@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.

C:\Users\avant>echo "Level 5 password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw" >> ~/bandit_notes.txt
The system cannot find the path specified.

C:\Users\avant>ssh bandit5@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit5@bandit.labs.overthewire.org's password:
Permission denied, please try again.
bandit5@bandit.labs.overthewire.org's password:


```
I listed for the files available
I tried to read "inhere", I thought it was a file.
Since it was a directory I cd into it
then I ask to list the files under the directory "inhere"
Now I needed to 'determine the type of file'
I needed to determine the type of each file because the challenge specifies that the password for the next level is stored in 
"the only human-readable file" in the directory.
So I entered the command manually to show me what each type of file is
The ASCII TEXT file or the file07 seemed different from the others so I read the file using the cat command
Then just like the previous challenges, I exited from the Bandit's server, I appended the new password onto a local text file. Then I logged into the
the bandit server using ssh key, entered the password as it asked me too and VOILA

## LEVEL 5 TO LEVEL 6
This one tested my patience a little
Like the previous challenges, I used ls to see what all directories or files are there. I found a directory called "inhere"
I cd into inhere
then I list files under this directory:
```
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
```
Next I needed to search for a file with very specific characteristics, I looked up what command shd be used to search for specific files and used this
```
bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable -exec file {} + | grep "ASCII text"
./maybehere07/.file2: ASCII text, with very long lines (1000)
```
And I saw that the specified file was .file 2
so I just used
```
cat .file2
```
I got my password : HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
So I exitted the server, appended the new password onto my local text file and then I used my ssh key to login to the server again
I entered the new password that I got and I was in.


## LEVEL 6 TO LEVEL 7

alr similar thing here again
I needed to find a very specific file with the given specifications
```
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
I had to learn how to do this specific file thing which was cool
It gave me a file name so I cat that
```
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
```
and I got the password:  morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
Then I exit the server, append the new password onto my local text file, enter the server again and then put password.
```
C:\Users\avant>"Level 7 password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj" >> ~/bandit_notes.txt
C:\Users\avant>ssh bandit7@bandit.labs.overthewire.org -p 2220
```

