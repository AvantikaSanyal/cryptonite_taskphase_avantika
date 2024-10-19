# LEARNING FROM DOCUMENTATION
pwn.college{Un0SK5P3P4WmWp6YydNE79dzGKn.dRjM5QDLykzN0czW}
simply  invoked the program "/challenge/challenge" and then passed the argument "--giveflag"

# LEARNING COMPLEX USAGE
pwn.college{ICGT38tTkNxqMfQXy3ZnrwWW57C.dVjM5QDLykzN0czW}
here basically what i used was "/challenge/challenge --printfile /flag"
passed printfile onto /challenge/challenge and then passed /flag onto printfile

# MANUAL READING 
"
       --nnwfwa NUM
              print the flag if NUM is 840"
pwn.college{AnnwJfwaNwzk8mhz-nKKjgNtguN.dRTM4QDLykzN0czW}
we did "man challenge" to read the manual
and then we did "/challenge/challenge --nnwfwa 840"

# SEARCHING MANUALS
pwn.college{Irlmo_XKQ56PekZI9W-3qntseyx.dVTM4QDLykzN0czW}
used man challenge
used /flag
then i did /challenge/challenge -n (according to the manual the -n was where the flag was found)

# SEARCHING FOR MANUALS
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

# HELPFUL PROGRAMS
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

 #  HELP FOR BUILTINS
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
