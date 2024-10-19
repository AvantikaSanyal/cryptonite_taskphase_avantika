# REDIRECTING OUTPUT
pwn.college{AiYUmZTWfsfhLPKBbpHKBpICrRB.dRjN1QDLykzN0czW}
very simple, just did echo PWN > COLLEGE because i wanted the word PWN to be redirected to COLLEGE

# REDIRECTING MORE OUTPUT
pwn.college{oxk3HOCKqz0q8DI-W5TG_T58-Gn.dVjN1QDLykzN0czW}
  hacker@piping~redirecting-more-output:~$ /challenge/run >myflag

   redirecting the output of "/challenge/run" to "myflag"
   this is what it showed :
   
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.

because it showed that i have successfully transferred the flag to "myflag" i just read that file and got my flag 

hacker@piping~redirecting-more-output:~$ cat myflag

# APPENDING OUTPUT
pwn.college{okmK312txvWRBHZiJfsm0Bcs8ec.ddDM5QDLykzN0czW}
 so they said first half in /challenge/run and second half of the flag in stdout
 redirected both to /home/hacker/the-flag like the question asked me to
 read the file using cat /home/hacker/the-flag
 
# REDIRECTING ERRORS
pwn.college{ARkhWMeAqU7EfNRdK671E0cf8RH.ddjN1QDLykzN0czW}
/challenge/run > myflag 2 > instructions
cat myflag

i redirected the output of /challenge/run to myflag from where i redirected its error to instructions
then i read myflag

# REDIRECTING INPUT
pwn.college{0L1pafFs7gQU6NZkQh-6hM0nh7U.dBzN1QDLykzN0czW}

here basically we needed to pass the value "COLLEGE" to the PWN file and then revert the PWN value too /challenge/run
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN


#  GREPPING STORED RESULTS
pwn.college{8iMCCNcfH46ZIwJ-1ApbKb4E3_J.dhTM4QDLykzN0czW}
/challenge/run > /tmp/data.txt
i redirected the output of /challenge/run to /tmp/data.txt as the question asked me to
then i kept doing grep "flag" /tmp/data.txt
but like i kept getting "flag" worda so like i was like why not do grep "pwn.college" /tmp/data.txt and it worked

# GREPPING LIVE OUTPUT
this was relatively simple considering the prev one
/challenge/run | grep pwn.college

# GREPPING ERRORS
pwn.college{ARkhWMeAqU7EfNRdK671E0cf8RH.ddjN1QDLykzN0czW}
2>&1grep pwn.college
as the question said i redirected the standard error  to the standard output then piped it. then i grepped for pwn.college since our flag starts with that
it didnt give any ouputs so i was like "ls" to see what files are there
i got :
hacker@piping~grepping-errors:~$ ls
COLLEGE  Desktop  PWN  a  instructions  myflag  not-the-flag  stdout  stdoyut  the-flag

then i saw the flag might be under myflag
cat myflag

this gave me a flag but its not the flag for this challenge
so i did cat the-flag
this didnt give me the correct flag either

GOT IT FINALLY OMG
pwn.college{U61TjfD-Y9Mka4ETDhB19zyKJ75.dVDM5QDLykzN0czW}
i wasnt piping it thats the issue
   hacker@piping~grepping-errors:~$ 2>&1grep pwn.college
   hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn

# DUPLICATED PIPED DATA WITH TEE
pwn.college{MPF3bojFD5TSebIvZdxcyQNBgqL.dFjM5QDLykzN0czW}
this one took me so long
     hacker@piping~duplicating-piped-data-with-tee:~$  /challenge/pwn | tee pwn_output | /challenge/college
Processing...
   WARNING: you are overwriting file pwn_output with tee's output...
   The input to 'college' does not contain the correct secret code! This code
   should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
   output of 'pwn' and figure out what the code needs to be.
   hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn_output
   Usage: /challenge/pwn --secret [SECRET_ARG]

     SECRET_ARG should be "MPF3bojF"

hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret MPF3bojF | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{MPF3bojFD5TSebIvZdxcyQNBgqL.dFjM5QDLykzN0czW}

Initial Attempt:

You piped the output of /challenge/pwn to /challenge/college via tee pwn_output.
tee created pwn_output and wrote the output to both the file and /challenge/college.
Error Message:

/challenge/college complained about missing a secret code, hinting at using tee to intercept the output.
Intercepting Output:

You used cat pwn_output to reveal the program's usage information:
/challenge/pwn requires a --secret flag followed by a specific secret code ("MPF3bojF").
Solving the Challenge:

You provided the correct secret code (MPF3bojF) using the --secret flag.
This satisfied /challenge/college and resulted in a success message with your flag.

# WRITING TO MULTIPLE PROGRAMS
pwn.college{YJE1T_EjGCAveHYCatVOS5XPN9-.dBDO0UDLykzN0czW}
The command >( /challenge/the ) creates a temporary named pipe and connects it to the standard input of /challenge/the. This allows you to treat the output of /challenge/the as if it were a file.
The command tee reads the output of /challenge/hack and writes it to its standard output (which is the terminal) and to the temporary named pipe created in the previous step.
The output of tee is then piped to /challenge/planet. This means that the output of /challenge/hack is now being sent to both /challenge/the and /challenge/planet simultaneously.
Both /challenge/the and /challenge/planet will receive the output of /challenge/hack as their input and can process it accordingly.


hacker@piping~writing-to-multiple-programs:~$ /challenge/hack |tee >(/challenge/the) | /challenge/planet


# SPLIT PIPING STDERR AND STDOUT
 /challenge/hack 2> >( /challenge/the ) | /challenge/planet
Process Substitution:

>( /challenge/the ) creates a temporary named pipe and connects it to the standard input of /challenge/the.
Redirection:

2> redirects the standard error (stderr) of /challenge/hack to the temporary named pipe created in step 1.
Piping:

The standard output (stdout) of /challenge/hack is piped to /challenge/planet using the | operator.
