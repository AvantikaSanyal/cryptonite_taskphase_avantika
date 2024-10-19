## THE ROOT
invoked pwn program using its absolute path
pwn.college{MfrxuF3A8KWHUs1OcpEIwlTB1IJ.dhzN5QDLykzN0czW}

## PROGRAM AND ABSOLUTE PATHS
Executing the 'run' file that is in the 'challenge' directory 

## POSITION THYSELF
executed the 'run' file in the 'challenge' directory then passed that to cd to navigate to where it is
pwn.college{wkS8wLTzRMwww05tPetXyG8CKCv.dZDN1QDLykzN0czW}

## POSITION ELSEWHERE
pwn.college{86JPp8en7WTJ2dNo-zBiXoMu2yA.ddDN1QDLykzN0czW}
user is navigating from home directory(~) to /some/new/directory. cd command is updating the address. we're executing a program in a specific directory. so we're using cd to navigate to the directory and executing the program from that directory


## POSITION YET ELSEWHERE
pwn.college{MCkBP7klkBqu5wOzHC5byk4nEos.dhDN1QDLykzN0czW}
user is navigating to yet another directory using cd and running the file from there
so ~ is for home directory. we're navigating to /usr/share/zoneinfo/posix/Asia using cd.
thus the command looks like cd /usr/share/zoneinfo/posix/Asia. and then we're running the challenege from there using /challenge/run

## IMPLICIT RELATIVE PATH- from /
pwn.college{sG-cjaxI-cMU09UgJ9VyV1XEogI.dlDN1QDLykzN0czW}
user is navigating using cd to '/' which is the root directory. then we run the challenge using challenge/run ,which is a relative path - relative to the root directory.

## EXPLICIT RELATIVE PATHS - from /
pwn.college{MzRZu58BuqLDuEHZQK2QLOULcIj.dBTN1QDLykzN0czW}
Relative paths are shorter and more convenient to work with for certain directories. the './' refers to current directory. With the command "./challenge/run" we tell the system to look inside the current directory and then run the challenge


## IMPLICIT RELATIVE PATHS
pwn.college{EaJhsGTTp6d5v5wddIZVrLddhZF.dFTN1QDLykzN0czW}
I first changed the current working directory using cd to challenge. Then i executed 'run' in the challenge directory. But because ive already entered the challenege directory in the previous step, I dont use the full "./challenge/run" like last time.
The "./" is used to tell the system that we are still in the afore mentioned "challenge" directory, so that is how it becomes a relative path - run relative to the challenege directory.

In the previous challenge, i was not previously in the challenge directory, so i had to "./challenge/run" - where i EXPLICITLY told it to enter the challenge directory and then run the chalenge.

## HOME SWEET HOME
pwn.college{UBxcs_fyhqi43Kiax7EDNbZvI48.dNzM4QDLykzN0czW}
So here again we cd / into my required directory. so
"cd /"
"./challenge/run" (explicitly telling the system to go to the challenge directory and run the file there)
then we're giving the ~/a which is basically /home/hacker/a (which is basically an absolute path - which is a complete and unambiguous path address to the required location starting from the root directory "/"

so it looks like "./challenge/run ~/a"
