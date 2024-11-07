# format string 0
flag : picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_dc0f36c4}

## My Approach
Relatively simple.
- I launched instance and copied the link "nc mimas.picoctf.net 60075" onto my terminal and pressed enter
- Then I was asked to input one of the three given choices, honestly went ahead and tried a variety of combinations
- got the flag
  
This was the code I got :
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>
#include <unistd.h>
#include <sys/types.h>

#define BUFSIZE 32
#define FLAGSIZE 64

char flag[FLAGSIZE];

void sigsegv_handler(int sig) {
    printf("\n%s\n", flag);
    fflush(stdout);
    exit(1);
}

int on_menu(char *burger, char *menu[], int count) {
    for (int i = 0; i < count; i++) {
        if (strcmp(burger, menu[i]) == 0)
            return 1;
    }
    return 0;
}

void serve_patrick();

void serve_bob();


int main(int argc, char **argv){
    FILE *f = fopen("flag.txt", "r");
    if (f == NULL) {
        printf("%s %s", "Please create 'flag.txt' in this directory with your",
                        "own debugging flag.\n");
        exit(0);
    }

    fgets(flag, FLAGSIZE, f);
    signal(SIGSEGV, sigsegv_handler);

    gid_t gid = getegid();
    setresgid(gid, gid, gid);

    serve_patrick();
  
    return 0;
}

void serve_patrick() {
    printf("%s %s\n%s\n%s %s\n%s",
            "Welcome to our newly-opened burger place Pico 'n Patty!",
            "Can you help the picky customers find their favorite burger?",
            "Here comes the first customer Patrick who wants a giant bite.",
            "Please choose from the following burgers:",
            "Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe",
            "Enter your recommendation: ");
    fflush(stdout);

    char choice1[BUFSIZE];
    scanf("%s", choice1);
    char *menu1[3] = {"Breakf@st_Burger", "Gr%114d_Cheese", "Bac0n_D3luxe"};
    if (!on_menu(choice1, menu1, 3)) {
        printf("%s", "There is no such burger yet!\n");
        fflush(stdout);
    } else {
        int count = printf(choice1);
        if (count > 2 * BUFSIZE) {
            serve_bob();
        } else {
            printf("%s\n%s\n",
                    "Patrick is still hungry!",
                    "Try to serve him something of larger size!");
            fflush(stdout);
        }
    }
}

void serve_bob() {
    printf("\n%s %s\n%s %s\n%s %s\n%s",
            "Good job! Patrick is happy!",
            "Now can you serve the second customer?",
            "Sponge Bob wants something outrageous that would break the shop",
            "(better be served quick before the shop owner kicks you out!)",
            "Please choose from the following burgers:",
            "Pe%to_Portobello, $outhwest_Burger, Cla%sic_Che%s%steak",
            "Enter your recommendation: ");
    fflush(stdout);

    char choice2[BUFSIZE];
    scanf("%s", choice2);
    char *menu2[3] = {"Pe%to_Portobello", "$outhwest_Burger", "Cla%sic_Che%s%steak"};
    if (!on_menu(choice2, menu2, 3)) {
        printf("%s", "There is no such burger yet!\n"); 
        fflush(stdout);
    } else {
        printf(choice2);
        fflush(stdout);
    }
}
```
too long, let's zoom down on one part
```

void sigsegv_handler(int sig) {
    printf("\n%s\n", flag);
    fflush(stdout);
    exit(1);
}
.
.
.
fgets(flag, FLAGSIZE, f);
    signal(SIGSEGV, sigsegv_handler);
```
from this section of the code I kind of realise that I need some segmentation fault to occur (again) for my flag to be printed.   
Took the hint given which said that this challenge is about format string vulnerabilities.     
So I asked chatgpt to point out where in the code are we focussing on format specifiers and that causing an error.

In this code, the section involving format specifiers is:
```
int count = printf(choice1);
```
and    
```
printf(choice2);
```
These lines use the printf function to output choice1 and choice2 directly, without specifying a format string (like "%s"). This can 
cause a format string vulnerability if the input contains format specifiers (such as %s, %d, etc.). In this case, any % in the user's
input could lead to unintended behavior. This exact unintended behaviour is the segmentation fault I need to get my flag.


## Terminal Output
```
avantikasanyal@LAPTOP-CFRE3HMA:~$ nc mimas.picoctf.net 60075
Welcome to our newly-opened burger place Pico 'n Patty! Can you help the picky customers find their favorite burger?
Here comes the first customer Patrick who wants a giant bite.
Please choose from the following burgers: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
Enter your recommendation: Gr%114d_Cheese
Gr                                                                                                           4202954_Cheese
Good job! Patrick is happy! Now can you serve the second customer?
Sponge Bob wants something outrageous that would break the shop (better be served quick before the shop owner kicks you out!)
Please choose from the following burgers: Pe%to_Portobello, $outhwest_Burger, Cla%sic_Che%s%steak
Enter your recommendation: Cla%sic_Che%s%steak
ClaCla%sic_Che%s%steakic_Che(null)
picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_dc0f36c4}
```

## What did I learn?
1. What are format specifiers?
   
           Format specifiers are placeholders in C used within functions like printf and scanf to control the type and format of
           data being output or input. They start with a percent sign (%) followed by a character that specifies the type
           of data. Format specifiers allow you to format integers, floating-point numbers, strings, characters, and more in specific ways.
3. What is a format string vulnerability?
   
           Format string vulnerabilities typically arise when user input is passed directly into a function without specifying a format.
           A format string vulnerability occurs when a program uses weird user input as the format string in functions like printf,
           scanf.
           When these functions take user input as the format string directly, they may interpret any % symbols in the input as format 
           specifiers


  ## Refernces
  1. ChatGPT
  2. https://owasp.org/www-community/attacks/Format_string_attack

## Errors Made
Honestly, the options that I had to enter I just did hit and trial there. I entered a variety of combinations before I got the right one   
I should have realised I just need the option with % sign in it to cause a format string vulnerability.
