# Basic Mod 2

my flag : picoCTF{1NV3R53LY_H4RD_C680BDC1}

## My Approach :

Read the challenge again :                                           
![image](https://github.com/user-attachments/assets/05d746d1-aaf4-4933-8f57-e64b96ed60e7) 

This is similar to basic mod 1. I made a similar code again :

```
#include <stdio.h>

// Function to compute gcd
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// Function to find the modular inverse of a mod m
int modular_inverse(int a, int m) {
    int m0 = m, x0 = 0, x1 = 1;
    if (gcd(a, m) != 1) {
        return -1; // Modular inverse does not exist if gcd is not 1
    }

    while (a > 1) {
        // Perform the division
        int q = a / m;
        int t = m;

        // Update m and a
        m = a % m, a = t;

        // Update x0 and x1
        t = x0;
        x0 = x1 - q * x0;
        x1 = t;
    }

    // Make x1 positive
    if (x1 < 0) {
        x1 += m0;
    }

    return x1;
}

int main() {
    // Define the character set: 1-26 -> A-Z, 27-36 -> 0-9, 37 -> _
    char character_set[] = {
        'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z',
        '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '_'
    };

    // List of numbers to process
    int numbers[] = {432, 331, 192, 108, 180, 50, 231, 188, 105, 51, 364, 168, 344, 195, 297, 342, 292, 198, 448, 62, 236, 342, 63};
    int num_count = sizeof(numbers) / sizeof(numbers[0]);

    // Result array to store decoded characters
    char result[num_count + 1]; // +1 for null terminator

    for (int i = 0; i < num_count; i++) {
        // Compute mod 41
        int mod_value = numbers[i] % 41;

        // Find modular inverse
        int inverse = modular_inverse(mod_value, 41);
        if (inverse == -1) {
            printf("Error: Modular inverse does not exist for %d\n", mod_value);
            return 1;
        }

        // Map the modular inverse to the character set
        if (inverse >= 1 && inverse <= 37) {
            result[i] = character_set[inverse - 1];
        } else {
            printf("Error: Invalid modular inverse %d\n", inverse);
            return 1;
        }
    }

    // Null-terminate the result string
    result[num_count] = '\0';

    // Output the result
    printf("Decoded string: %s\n", result);

    return 0;
}
```
Running this gave me my flag.                                           
![image](https://github.com/user-attachments/assets/f28aff78-83f2-4a03-acb9-62a8804776b9)


### Inverse Mod
 For a given integer 
𝑎 a and a modulus 𝑚, the modular inverse of 𝑎 is an integer 𝑥 such that:
![image](https://github.com/user-attachments/assets/37d42943-5f6d-4d30-bc5e-d84bb31ad672).

## Errors 
None

## Resources
ChatGPT

## What did I learn ?
What is an inverse mod

