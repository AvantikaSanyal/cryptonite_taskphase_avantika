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

SEARCGING MANUALS
pwn.college{Irlmo_XKQ56PekZI9W-3qntseyx.dVTM4QDLykzN0czW}
used man challenge
used /flag
then i did /challenge/challenge -n (according to the manual the -n was where the flag was found)



















