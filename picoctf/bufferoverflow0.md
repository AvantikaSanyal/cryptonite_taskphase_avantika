# Buffer Overflow 0
This was easy after I understood what's happening (which took some asking around).   

flag : picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}

## My Approach
I launched the instance and got my code.
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}

void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
}

int main(int argc, char **argv){
  
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }
  
  fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler); // Set up signal handler
  
  gid_t gid = getegid();
  setresgid(gid, gid, gid);


  printf("Input: ");
  fflush(stdout);
  char buf1[100];
  gets(buf1); 
  vuln(buf1);
  printf("The program will exit now\n");
  return 0;
}
```
thats way too long, let's focus on one specific part     
```
void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}

void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
.
.
.
fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler);
```
So from here I can say that the function sigsegv_handler prints my flag. And it requires a segmentation fault to occur(OVERFLOW IT)    
The void vuln function asks me for a 16 character input.
This is an OVERFLOW challenge, so I gotta overflow with my input i.e. more than 16 characters.
That is all is the crux of this challenge.

- step 1 : run the instance    
- step 2 : observe the code. Notice what is my overflow criteria     
- step 3 : open my ubuntu terminal and paste the link " nc saturn.picoctf.net 62210 "    
- step 4 : it asks for input. give a greater than 16 character input     
- step 5 : find your flag


  ## Terminal Output
  

  ![bufferoverflow0](https://github.com/user-attachments/assets/be81ef82-2c2e-4c27-be27-18260e1278ea)
  ![image](https://github.com/user-attachments/assets/0bafee12-ebfa-49cb-9b3e-34a048c7651d)


## What I learned
My friend gave this wonderful visual for overflow.  
Say you have the puri in pani puri. Imagine it has a small hole. To find out the hole, I overfill my puri with pani and see from where the water drips out.

### overflow
It is essentially looping the number from the highest possible value to the lowest possible value by adding past the maximum possible length.

## References
https://www.youtube.com/watch?v=Dbbh_lrbgAU

## Errors I made
I was trying to run my program in command prompt instead of Ubuntu for Linux 
