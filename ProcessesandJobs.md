# LISTING PROCESSES
  pwn.college{AuChQjRP0aAYF2RIFwGvh-gSqyl.dhzM4QDLykzN0czW}
  i did ps -ef and was faced with 
     UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  1 13:45 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
root           7       1  0 13:45 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 13:45 ?        00:00:00 /challenge/13440-run-30395
root          72      68  0 13:45 ?        00:00:00 sleep 6h
hacker        73       0  0 13:45 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 13:45 pts/0    00:00:00 ps -ef

then i looked for one with /challenge at the start and then i ran : /challenge/13440-run-30395

# KILLING PROCESSES
pwn.college{8-In2RVerrG-Oy1HXh1k1M7BCnH.dJDN4QDLykzN0czW}

i first tried ps -e | /challenge/dont_run
but that did nothing
so i did ps aux | /challenge/dont_run
  hacker        73  0.0  0.0   4976  3200 ?        Ss   14:20   0:00 /challenge/dont_run
  hacker        97  0.0  0.0   4140  2560 pts/0    S+   14:22   0:00 grep --color=auto /challenge/dont_run
then i did kill 73 and kill 97 (both cus i didnt know which one)
then i did /challenge/run

# INTERRUPTING PROCESSES
pwn.college{cWleoDHf8ZFivRnedoDVIyswZ2D.dNDN4QDLykzN0czW}

I did /challenge/run 
now the challenge is running so we gotta interrupt it
Ctrl-C

# RESUMING PROCESS
pwn.college{A5Ab0zsl4LkAS3WrrSFVRsljzEH.dZDN4QDLykzN0czW}

here i did : /challenge/run
i suspended doing ctrl z
then i did fg and i got my flag

# BACKGROUNDING PROCESS
pwn.college{YENBxmOvxh_2__7cqj3ByJLAQpF.ddDN4QDLykzN0czW}

   /challenge/run
   then i suspended it using ctrl z
   then i made it run in the backgriund with "bg"
   to check what is happening with the program i ran "ps -o user,pid,stat,cmd"
   then i ran the challenge using /challenge/run again

   # FOREGROUNDING PROCESS
   pwn.college{YsH75Cl8kS9oiCZiUK2IQ0Mgd_G.dhDN4QDLykzN0czW}

   so i first ran /challenge/run
   then they showed me "To pass this level, you need to suspend me, resume the suspended process in the
             background, and *then* foreground it without re-suspending it! You can
             background me with Ctrl-Z (and resume me in the background with 'bg') or, if
             you're not ready to do that for whatever reason, just hit Enter and I'll exit!"
   so then as asked i suspended it using ctrl z
   then i used "bg" to run in the background
   then to swap it into foreground i used "fg"

# STARTING BACKGROUND PROCESSES
pwn.college{shx3lXKtccSNssxuy0zW9JM9XNv.dlDN4QDLykzN0czW}

i needed to run the program directly in the background so i used /challenge/run 

# PROCESS EXIT CODES
pwn.college{gGiBumCN1Cl0bKOu_WJPrna81CZ.dljN4UDLykzN0czW}
i ran /challenge/get-code
it exited with a return code
so i wanted to see what that retrun code was
then i did echo $? (as given in tge example)
i got the value 255
then i did /challenge/submit-code 255 and i got my flag
