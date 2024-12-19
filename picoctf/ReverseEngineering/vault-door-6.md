# vault door 6

flag : picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc}

## My Approach
- I first went thru the given code properly      
```
import java.util.*;

class VaultDoor6 {
    public static void main(String args[]) {
        VaultDoor6 vaultDoor = new VaultDoor6();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Dr. Evil gave me a book called Applied Cryptography by Bruce Schneier,
    // and I learned this really cool encryption system. This will be the
    // strongest vault door in Dr. Evil's entire evil volcano compound for sure!
    // Well, I didn't exactly read the *whole* book, but I'm sure there's
    // nothing important in the last 750 pages.
    //
    // -Minion #3091
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
        };
        for (int i=0; i<32; i++) {
            if (((passBytes[i] ^ 0x55) - myBytes[i]) != 0) {
                return false;
            }
        }
        return true;
    }
}
```

- Let us see what the crux logic is :                          
![image](https://github.com/user-attachments/assets/61cbb010-57cd-46ac-997b-5add69df9dfd)                    
- So we see here that each byte is being XORed with 0x55. If and only if the difference of the XOR result and myBytes gives 0, then it will return true.         
- So that means, the XOR results should be equal to myBytes
            
This is what is stored in myBytes :                          
![image](https://github.com/user-attachments/assets/8fed2bb2-1e7f-49c2-9f18-b9a67c0e5fb5)        

However, we also have a given hint              
![image](https://github.com/user-attachments/assets/05d17283-5c17-4955-9b90-f88584703274)           

- So if passBytes ^ 0x55 is myBytes, then myBytes ^ 0x55 is passBytes
                
And from here ![image](https://github.com/user-attachments/assets/5b07e4d5-412e-40a9-9c10-2f91f98c275f)  we can see that passBytes is the password or something like that       
So I ask ChatGPT to XOR the bytes with 0x55 and return it to me   

ChatGPT gave me this code :
```
hex_values = [
    0x3b, 0x65, 0x21, 0x0a, 0x38, 0x00, 0x36, 0x1d,
    0x0a, 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0x0a,
    0x21, 0x1d, 0x61, 0x3b, 0x0a, 0x2d, 0x65, 0x27,
    0x0a, 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
]

# XOR each value with 0x55 and convert to text
xor_key = 0x55
xor_result = ''.join(chr(h ^ xor_key) for h in hex_values)
print(xor_result)
```

After running the code, I got my flag.
![image](https://github.com/user-attachments/assets/34ef3f85-bfcf-4d7e-9f26-35e51e588595)               

## Resources
ChatGPT

## Errors
None really, for this challenge we just needed to understand the logic

## What did I learn?
Important XOR logic : *If X ^ Y = Z, then Z ^ Y = X*       




