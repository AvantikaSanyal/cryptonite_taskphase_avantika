# MATCHING WITH *
pwn.college{M4JBpmN-H3WXDmCZViylpM0sKZ7.dFjM4QDLykzN0czW}
     hacker@globbing~matching-with-:~$ cd /ch*
     hacker@globbing~matching-with-:/challenge$ /challenge/run
i was asked to cd into challenge but using * and keeping it shorter than four characters so i went with "/ch*"
so then i had entered the /challenge directory after which i simply ran "/challenge/run"

# MATCHING WITH ?
pwn.college{shzz1wgLYHZHi7NPXuxbEXOOVP4.dJjM4QDLykzN0czW}
       hacker@globbing~matching-with-:~$ cd /?ha??enge
       hacker@globbing~matching-with-:/challenge$ /challenge/

This was similar to the previous one where except for "/ch*" i simply did "/?ha??enge" like they asked me to

# MATCHING WITH []
pwn.college{wHhi9Ew75rhqGQo5PkKrV9QJlu2.dNjM4QDLykzN0czW}
   cd/challenge/files
   /challenge/run file_[bash]

this was pretty straight forward, i changed my directory as asked and then i searched for file_a,file_b,file_s,file_h with file_[bash]


# MATCHING PATHS WITH []
pwn.college{A446B-R5sZCGNBiFr4Vx1wgsRX0.dRjM4QDLykzN0czW}
I tried running: /challenge/run file_[bash] but got an error because you weren't in the right folder (/home/hacker).
I changed the folder to /home/hacker, as the error asked you to but that gave me another error cus that is not where the required files were Since the files are in /challenge/files, I had to include that location when running the command:
/challenge/run /challenge/files/file_[bash]

# MIXING GLOBS
pwn.college{gP5JS1Af8IWXENZ8vQHZx3XT-Xr.dVjM4QDLykzN0czW}
got stuck here SO MANY TIMES
anyways
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*

i moved into the directory of /challenge/files
then i did /challenge/run [cep]*
basically challenge -c*
          educational -e*
          pwning - p*

# EXCLUSIONARY GLOBBING
pwn.college{UmPdTLjQxIPikXo9CR2Qt7a3YFD.dZjM4QDLykzN0czW}
" /challenge/files$ /challenge/run [!pwn]* "
same thing as the last one except i wanted to NOT include the p,w,n ones so i simply did "!"
