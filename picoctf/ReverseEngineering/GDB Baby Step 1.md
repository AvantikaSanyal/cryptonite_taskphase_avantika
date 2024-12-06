# GDB Baby Step 1
flag : picoCTF{549698}

## Hint :
1. gdb is a very good debugger to use for this problem and many others!
2. main is actually a recognized symbol that can be used with gdb commands.
   
## My Approach :
1. So I first downloaded my source code
2. Then I tried a lot to read the file which was stored as *debugger0_a* but that didnt work. Nothing worked. I then did
   ```
   sudo apt update
   ```
   and also
   ```
   sudo apt install gdb
   ```
3. Once that was done, I tried to find where my *debugger0_a* file was. It was not in the home directory, so I moved it into the home directory. Maybe that is why I wasn't able to use the command *file* to read it?
   ```
   avantikasanyal@LAPTOP-CFRE3HMA:~$ mv /mnt/c/Users/avant/Downloads/debugger0_a /home/avantikasanyal/
   ```
   ![image](https://github.com/user-attachments/assets/9dce5895-1592-4aae-ba0d-ca8c5a101617)
4. Since I had already installed GDB from the hint, I used the command
   ```
    gdb ./debugger0_a
   ```
   *The command gdb ./debugger0_a starts the GNU Debugger (GDB) and loads the binary file debugger0_a for debugging.*

5. ```
   disassemble main
   ```

6. I got this 
![image](https://github.com/user-attachments/assets/929dd3e7-3fe9-4b89-b975-59dbc3f2d080)

7. Then I did
   ```
   (gdb) print 0x86342
   ```
   That was my flag value

   ## Terminal Output
   ```
   avantikasanyal@LAPTOP-CFRE3HMA:~$ ls
   README.md  bandit_notes.txt  cryptonite_taskphase_avantika  flag.txt  instructions  key  key.pub  myflag
   avantikasanyal@LAPTOP-CFRE3HMA:~$ find ~ -name "debugger0_a"
   avantikasanyal@LAPTOP-CFRE3HMA:~$ pwd
   /home/avantikasanyal
   avantikasanyal@LAPTOP-CFRE3HMA:~$ mv /mnt/c/Users/avant/Downloads/debugger0_a /home/avantikasanyal/
   avantikasanyal@LAPTOP-CFRE3HMA:~$ ls /home/avantikasanyal/
   README.md         cryptonite_taskphase_avantika  flag.txt      key      myflag
   bandit_notes.txt  debugger0_a                    instructions  key.pub
   avantikasanyal@LAPTOP-CFRE3HMA:~$ cd /home/avantikasanyal
   avantikasanyal@LAPTOP-CFRE3HMA:~$ gdb ./debugger0_a
    GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
    Copyright (C) 2022 Free Software Foundation, Inc.
    License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
    This is free software: you are free to change and redistribute it.
     There is NO WARRANTY, to the extent permitted by law.
   Type "show copying" and "show warranty" for details.
   This GDB was configured as "x86_64-linux-gnu".
   Type "show configuration" for configuration details.
   For bug reporting instructions, please see:
   <https://www.gnu.org/software/gdb/bugs/>.
   Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

   For help, type "help".
   Type "apropos word" to search for commands related to "word"...
     Reading symbols from ./debugger0_a...
     (No debugging symbols found in ./debugger0_a)
   (gdb) disassemble main
   Dump of assembler code for function main:
   0x0000000000001129 <+0>:     endbr64
   0x000000000000112d <+4>:     push   %rbp
   0x000000000000112e <+5>:     mov    %rsp,%rbp
   0x0000000000001131 <+8>:     mov    %edi,-0x4(%rbp)
   0x0000000000001134 <+11>:    mov    %rsi,-0x10(%rbp)
   0x0000000000001138 <+15>:    mov    $0x86342,%eax
   0x000000000000113d <+20>:    pop    %rbp
   0x000000000000113e <+21>:    ret
   End of assembler dump.
   (gdb) x/s 0x86342
     0x86342:        <error: Cannot access memory at address 0x86342>
   (gdb) print 0x86342
   $1 = 549698
```
 ```
## What did I learn?
1. What is GDB?
        GDB is often used to analyze binary files and find hidden data (such as flags) by reverse-engineering the program.
        I installed GDB to interact with the provided binary files and debug the program to understand its inner workings.           
2. Commands used in GDB :          
     a) gdb ./debugger0_a         
        Starts GDB and loads the debugger0_a binary for analysis.        
     b) disassemble main         
        Displays the assembly code for the main function of the program.        
     c) print 0x86342       
        Prints the value stored at the memory address 0x86342

## Errors
1. I tried opening a file from a directory I wasn't in, so I had to move the file.
