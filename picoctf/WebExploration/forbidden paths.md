# Forbidden Paths
flag : picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}

## My Approach :
First I tried to enter /flag.txt in my search bar. It showed me:         

![image](https://github.com/user-attachments/assets/0a72f590-dad1-4cfe-a19f-4702b599889d)            

Then I read the description of the challenge 

### Challenge Description : 
Can you get the flag?
We know that the website files live in /usr/share/nginx/html/ and the flag is at /flag.txt 
but the website is filtering absolute file paths. Can you get past the filter to read the flag?

Oh okay, relative and absolute paths like we did in Linux Luminarium.    

Sweet.

Relative paths basically are used to open files relative to the directory you're already in. I can simply use "." for current directory and
".." for the directory before the current one.

sooo I looked into the absolute address that they have given :
```
usr/share/nginx/html/
```
So I need like, four parts.     
Hence I enter :
```
../../../../flag.txt
```
So this will access the flag.txt, using its relative paths. The dots will refer to above directories that were open. And we used four parts
like given in the absolute path.

![image](https://github.com/user-attachments/assets/67776a5a-2c23-4d4e-855a-0d5975010e37)

## What did I learn?
1. Absolute Path
- Definition: The complete address to a file or folder starting from the root directory.
- starts with "/" which is root directory
- Example:
/home/user/Documents/file.txt            
Think of it as the full address of your house, like "123 Main Street, City, Country."

2. Relative Path
- Definition: The address to a file or folder relative to your current location in the file system.
- doesn't start with "/"
- Example:
If you're in /home/user/ then              
../file.txt means "go up one folder and look for file.txt."
It’s like saying, “The kitchen is next to the living room,” instead of giving the full house address.

## Errors :
I tried using 
```
././././flag.txt
```
Um, didn't work. I guess the flag wasn't in the current directory and I needed to go up some directories. Whatever, this was cutesy.





