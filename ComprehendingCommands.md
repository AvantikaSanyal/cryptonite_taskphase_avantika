# CAT THE COMMAND NOT THE PET
pwn.college{UlnsfzsJpOr-Q8x2pbjbmF9EDSL.dFzN1QDLykzN0czW}
so basically i used "cat" to read the "flag" file where my flag was stored

# CATTING ABSOLUTE PATHS
pwn.college{kybDDZwE-IDjTp3rTazUOayldVQ.dlTM5QDLykzN0czW}
here we used the "cat" to read the flag in the absloute path "/flag"
"cat /flag"


# MORE CATTING PRACTICE
pwn.college{0vZK6loDjZv1NOrbMF3ujg0jZBF.dBjM5QDLykzN0czW}
i used "cat" to ouput the contents at the address of /usr/share/enchant-2/flag

# GREPPING FOR NEEDLE IN A HAYSTACK
pwn.college{gFYQ9cNa76XRfa5TxBC88NkHhSe.ddTM4QDLykzN0czW}
used " grep pwn.college /challenge/data.txt" to find the file with the line "pwn.college"  among thousands of lines in "challenge/data.txr"

# LISTING FILES
pwn.college{wygHIZPFygLix34D118EBYKmI1O.dhjM4QDLykzN0czW}
i listed the files under challenge using "ls /challenge"
then i was shown what "run" was renamed as
i used "/challenge/21464-renamed-run-14389" and found the flag

# TOUCHING FLAGS
pwn.college{YeonnGs9hs_eGX7sBfZvAMNcj0k.dBzM4QDLykzN0czW}
here the steps were:
cd /tmp
ls
touch pwn (or) college
/challenge/run

Baically we went into the tmp directory, created "college" and "pwn" and ran the challenge

# REMOVING FILES
pwn.college{kmBU6a8jyFUobwiSPPJmfJeP09M.dZTOwUDLykzN0czW}
simply using "rm delete_me" to remove the delete_me file 

# HIDDEN FILES
pwn.college{Mf4rf4qplkfIdDuGoUurc7793at.dBTN4QDLykzN0czW}
used "ls -a /" to display the hidden files in "/"
then " cat /.flag-11313194731821" using cat to read the flag file

# MAKING DICTIONARIES
pwn.college{MzS-NHvWbIfPvXtdegWG_90lPoz.dFzM4QDLykzN0czW}
we went to tmp using cd "cd /tmp"
then we displayed whats in "tmp" ls
then we make a dictiornary in tmp using "mkdir pwn"
then simply "touch college" to make the file
and then run challenge

 
# FINDING FILES
pwn.college{sabJdKMw6bZNLBOlnUZQAex4LVU.dJzM4QDLykzN0czW}
we first did " find / -name flag" and got a list of every place flag is
ignoring the ones where we were denied permission
i did cat for every other location


# AN EPIC FILESYSTEM QUEST
pwn.college{k7lKiqQnycEEyGx9I3BHIw15Yeb.dljM4QDLykzN0czW}
i cd or ls or cat into files as needed (there were like 500 steps i genuinely cant list them)

#   LINKING FILES
pwn.college{k6N77bfltXrwF24Jowntcdm5LZT.dlTM1UDLykzN0czW}

"hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag"

removed the not-the-flag then create a not-the-flag that we're soft linking to the flag. then we run challenge/catflag which is 
linked to not-the-flag thus it runs flag
