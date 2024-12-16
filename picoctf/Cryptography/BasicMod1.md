# Basic Mod 1

flag : picoCTF{R0UND_N_R0UND_B6B25531}

## My Approach :

First I read the challenge carefully.             

![image](https://github.com/user-attachments/assets/0c0607e9-89a9-4476-96e1-4a93586c7b6b)

Then I got the numbers from the text file .
```
165 248 94 346 299 73 198 221 313 137 205 87 336 110 186 69 223 213 216 216 177 138
```

Then I made a simple C code, the logic of which is :
1. I made an array and stored the numbers given
   ![image](https://github.com/user-attachments/assets/c0e645f5-9b74-463d-ada4-f996fe869179)

2. Then I made a character set in accordance to the challenge's need. For example, first 25 characters would be uppercase letters, next 9 are digits and the last character in the set would be an underscore
   ![image](https://github.com/user-attachments/assets/ea4b9c37-85b6-487e-b2ad-921383276202)

3. Then I made a for loop, to run thru the array with the given numbers
   
4. In the for loop, the modulus of the number with 37 is being taken, then whatever value we get we are taking the corresponding character from the character set at that position.
   ![image](https://github.com/user-attachments/assets/b71585a9-0429-4f9e-89d3-288bf9788f86)

   The code is :
   ```
   #include <stdio.h>

   int main() {
    // Define the character set: 0-25 -> A-Z, 26-35 -> 0-9, 36 -> _
    char character_set[] = {
        'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z',
        '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '_'
    };

    // List of numbers to process
    int numbers[] = {165, 248, 94, 346, 299, 73, 198, 221, 313, 137, 205, 87, 336, 110, 186, 69, 223, 213, 216, 216, 177, 138};
    int num_count = sizeof(numbers) / sizeof(numbers[0]);

    // Result array to store decoded characters
    char result[num_count + 1]; // +1 for null terminator

    // Compute mod 37 and map to character set
    for (int i = 0; i < num_count; i++) {
        int mod_value = numbers[i] % 37;
        result[i] = character_set[mod_value];
    }

    // Null-terminate the result string
    result[num_count] = '\0';

    // Output the result
    printf("Decoded string: %s\n", result);

    return 0;
```
```
## Errors :
None, pretty direct.

## Resources :
ChatGPT






