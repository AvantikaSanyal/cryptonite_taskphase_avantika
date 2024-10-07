# cryptonite_taskphase_avantika
INTRO TO COMMANDS
i invoked my frist command of 'hello'
pwn.college{0zsEufSmA-0j4vV1IdJH2Yoi6pg.ddjNyUDLykzN0czW}

INTRO TO ARGUMENTS
i passed hackers thru the command hello
pwn.college{09Sv9MphdyS9RG9-Mf7izISYiei.dhjNyUDLykzN0czW}

THE ROOT
invoked pwn program using its absolute path
pwn.college{MfrxuF3A8KWHUs1OcpEIwlTB1IJ.dhzN5QDLykzN0czW}

PROGRAM AND ABSOLUTE PATHS
Executing the 'run' file that is in the 'challenge' directory 

POSITION THYSELF
executed the 'run' file in the 'challenge' directory then passed that to cd to navigate to where it is
pwn.college{wkS8wLTzRMwww05tPetXyG8CKCv.dZDN1QDLykzN0czW}

POSITION ELSEWHERE
pwn.college{86JPp8en7WTJ2dNo-zBiXoMu2yA.ddDN1QDLykzN0czW}
user is navigating from home directory(~) to /some/new/directory. cd command is updating the address. we're executing a program in a specific directory. so we're using cd to navigate to the directory and executing the program from that directory


POSITION YET ELSEWHERE
pwn.college{MCkBP7klkBqu5wOzHC5byk4nEos.dhDN1QDLykzN0czW}
user is navigating to yet another directory using cd and running the file from there
so ~ is for home directory. we're navigating to /usr/share/zoneinfo/posix/Asia using cd.
thus the command looks like cd /usr/share/zoneinfo/posix/Asia. and then we're running the challenege from there using /challenge/run

IMPLICIT RELATIVE PATH- from /
pwn.college{sG-cjaxI-cMU09UgJ9VyV1XEogI.dlDN1QDLykzN0czW}
user is navigating using cd to '/' which is the root directory. then we run the challenge using challenge/run ,which is a relative path - relative to the root directory.

EXPLICIT RELATIVE PATHS - from /
pwn.college{MzRZu58BuqLDuEHZQK2QLOULcIj.dBTN1QDLykzN0czW}
Relative paths are shorter and more convenient to work with for certain directories. the './' refers to current directory. With the command "./challenge/run" we tell the system to look inside the current directory and then run the challenge


IMPLICIT RELATIVE PATHS
pwn.college{EaJhsGTTp6d5v5wddIZVrLddhZF.dFTN1QDLykzN0czW}
I first changed the current working directory using cd to challenge. Then i executed 'run' in the challenge directory. But because ive already entered the challenege directory in the previous step, I dont use the full "./challenge/run" like last time.
The "./" is used to tell the system that we are still in the afore mentioned "challenge" directory, so that is how it becomes a relative path - run relative to the challenege directory.

In the previous challenge, i was not previously in the challenge directory, so i had to "./challenge/run" - where i EXPLICITLY told it to enter the challenge directory and then run the chalenge.

HOME SWEET HOME
pwn.college{UBxcs_fyhqi43Kiax7EDNbZvI48.dNzM4QDLykzN0czW}
So here again we cd / into my required directory. so
"cd /"
"./challenge/run" (explicitly telling the system to go to the challenge directory and run the file there)
then we're giving the ~/a which is basically /home/hacker/a (which is basically an absolute path - which is a complete and unambiguous path address to the required location starting from the root directory "/"

so it looks like "./challenge/run ~/a"


CAT THE COMMAND NOT THE PET
pwn.college{UlnsfzsJpOr-Q8x2pbjbmF9EDSL.dFzN1QDLykzN0czW}
so basically i used "cat" to read the "flag" file where my flag was stored

CATTING ABSOLUTE PATHS
pwn.college{kybDDZwE-IDjTp3rTazUOayldVQ.dlTM5QDLykzN0czW}
here we used the "cat" to read the flag in the absloute path "/flag"
"cat /flag"


MORE CATTING PRACTICE
pwn.college{0vZK6loDjZv1NOrbMF3ujg0jZBF.dBjM5QDLykzN0czW}
i used "cat" to ouput the contents at the address of /usr/share/enchant-2/flag

GREPPING FOR NEEDLE IN A HAYSTACK
pwn.college{gFYQ9cNa76XRfa5TxBC88NkHhSe.ddTM4QDLykzN0czW}
used " grep pwn.college /challenge/data.txt" to find the file with the line "pwn.college"  among thousands of lines in "challenge/data.txr"

LISTING FILES
pwn.college{wygHIZPFygLix34D118EBYKmI1O.dhjM4QDLykzN0czW}
i listed the files under challenge using "ls /challenge"
then i was shown what "run" was renamed as
i used "/challenge/21464-renamed-run-14389" and found the flag

TOUCHING FLAGS
pwn.college{YeonnGs9hs_eGX7sBfZvAMNcj0k.dBzM4QDLykzN0czW}
here the steps were:
cd /tmp
ls
touch pwn (or) college
/challenge/run

Baically we went into the tmp directory, created "college" and "pwn" and ran the challenge

REMOVING FILES
pwn.college{kmBU6a8jyFUobwiSPPJmfJeP09M.dZTOwUDLykzN0czW}
simply using "rm delete_me" to remove the delete_me file 

HIDDEN FILES
pwn.college{Mf4rf4qplkfIdDuGoUurc7793at.dBTN4QDLykzN0czW}
used "ls -a /" to display the hidden files in "/"
then " cat /.flag-11313194731821" using cat to read the flag file

MAKING DICTIONARIES
pwn.college{MzS-NHvWbIfPvXtdegWG_90lPoz.dFzM4QDLykzN0czW}
we went to tmp using cd "cd /tmp"
then we displayed whats in "tmp" ls
then we make a dictiornary in tmp using "mkdir pwn"
then simply "touch college" to make the file
and then run challenge


FINDING FILES
pwn.college{sabJdKMw6bZNLBOlnUZQAex4LVU.dJzM4QDLykzN0czW}
we first did " find / -name flag" and got a list of every place flag is
ignoring the ones where we were denied permission
i did cat for every other location


AN EPIC FILESYSTEM QUEST
pwn.college{k7lKiqQnycEEyGx9I3BHIw15Yeb.dljM4QDLykzN0czW}
i cd or ls or cat into files as needed (there were like 500 steps i genuinely cant list them)

LINKING FILES
pwn.college{k6N77bfltXrwF24Jowntcdm5LZT.dlTM1UDLykzN0czW}

"hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag"

removed the not-the-flag then create a not-the-flag that we're soft linking to the flag. then we run challenge/catflag which is linked to not-the-flag thus it runs flag

LEARNING FROM DOCUMENTATION
pwn.college{Un0SK5P3P4WmWp6YydNE79dzGKn.dRjM5QDLykzN0czW}
simply  invoked the program "/challenge/challenge" and then passed the argument "--giveflag"

LEARNING COMPLEX USAGE
pwn.college{ICGT38tTkNxqMfQXy3ZnrwWW57C.dVjM5QDLykzN0czW}
here basically what i used was "/challenge/challenge --printfile /flag"
passed printfile onto /challenge/challenge and then passed /flag onto printfile

MANUAL READING 
"
       --nnwfwa NUM
              print the flag if NUM is 840"
pwn.college{AnnwJfwaNwzk8mhz-nKKjgNtguN.dRTM4QDLykzN0czW}
we did "man challenge" to read the manual
and then we did "/challenge/challenge --nnwfwa 840"

SEARCHING MANUALS
pwn.college{Irlmo_XKQ56PekZI9W-3qntseyx.dVTM4QDLykzN0czW}
used man challenge
used /flag
then i did /challenge/challenge -n (according to the manual the -n was where the flag was found)

HELPFUL PROGRAMS
pwn.college{oUeKH2j2KE5zmOsu8DTGFZgO8n1.dZTM4QDLykzN0czW}
i used "man man" to read the manual
then i was like i need to search for the flag "/flag"
then i saw that " man -k printf
           Search the short descriptions and manual page names for the keyword printf as regular  expression.   Print
           out any matches.  Equivalent to apropos printf."
so i first tried "man -k"
but that didnt work
so i tried passing the command "man -k flag"
then i saw this  "oejzmsugnd (1)       - print the flag!"
then " man oejzmsugnd"
then "--oejzms NUM
              print the flag if NUM is 225"
then "/challenge/challenge  --oejzms 225"

HELPFUL PROGRAMS
pwn.college{Mk5wARW7Uw4sBZW-0kRY8g2H1zB.ddjM4QDLykzN0czW}
Here's what we did :
"/challenge/challenge --h"
this displayed:
" -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag"

  so i saw that i need to do "-p" 
  "/challenge/challenge -p"
  It gave me the secret value to be : 574
  "hacker@man~helpful-programs:~$ /challenge/challenge -g 574"

  HELP FOR BUILTINS
  pwn.college{8L6FMlNuDJwMgutgjgfTpHr2pyZ.dRTM5QDLykzN0czW}
  i did "challenge help"
  this gave me: challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "8L6FMlNu".

so i directly did challenge --secret 8L6FMlNu

MATCHING WITH *
pwn.college{M4JBpmN-H3WXDmCZViylpM0sKZ7.dFjM4QDLykzN0czW}
     hacker@globbing~matching-with-:~$ cd /ch*
     hacker@globbing~matching-with-:/challenge$ /challenge/run
i was asked to cd into challenge but using * and keeping it shorter than four characters so i went with "/ch*"
so then i had entered the /challenge directory after which i simply ran "/challenge/run"

MATCHING WITH ?
pwn.college{shzz1wgLYHZHi7NPXuxbEXOOVP4.dJjM4QDLykzN0czW}
       hacker@globbing~matching-with-:~$ cd /?ha??enge
       hacker@globbing~matching-with-:/challenge$ /challenge/

This was similar to the previous one where except for "/ch*" i simply did "/?ha??enge" like they asked me to

MATCHING WITH []
pwn.college{wHhi9Ew75rhqGQo5PkKrV9QJlu2.dNjM4QDLykzN0czW}
   cd/challenge/files
   /challenge/run file_[bash}

this was pretty straight forward, i changed my directory as asked and then i searched for file_a,file_b,file_s,file_h with file_[bash]






















