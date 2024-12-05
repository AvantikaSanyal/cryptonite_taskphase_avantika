# Vault Door 3
Flag : jU5t_a_s1mpl3_an4gr4m_4_u_1fb380

## My Approach
well first I read the code.
```
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
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

    // Our security monitoring team has noticed some intrusions on some of the
    // less secure doors. Dr. Evil has asked me specifically to build a stronger
    // vault door to protect his Doomsday plans. I just *know* this door will
    // keep all of those nosy agents out of our business. Mwa ha!
    //
    // -Minion #2671
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm18gb41_u_4_mfr340");
    }
}
```
blah blah blah.
we need two specific part of this code : 
1. the stored string          

![image](https://github.com/user-attachments/assets/1b905c12-5f4c-4fac-a796-9fa5e8660e59)      

2. the modifications this string undergoes :                       

![image](https://github.com/user-attachments/assets/6cb6f832-2c3e-4e5a-82a0-ee36b724dc58)               

basic index looping shit.



### first loop
![image](https://github.com/user-attachments/assets/a489a158-44b6-4ab9-8d3a-ac8e4c268513)           
first 8 characters remain the same.        
new pw : jU5t_a_s

### second loop 
![image](https://github.com/user-attachments/assets/d99ebb18-1a8a-4d21-b439-c28673785777)        
i starts at 8      
this loop now adds to our new pw string the characters at positions 15,14,13,12,11,10,9,8             
new pw : jU5t_a_s1mpl3_a

### third loop
![image](https://github.com/user-attachments/assets/4c2f59c6-c53f-403c-b566-a1e48b484744)         
i starts at 16           
this loop now adds to our new pw string the characters at positions 30 to 15.         
new pw : jU5t_a_s1mpl3_an4gr4m_4_u_1fb3

### fourth loop
![image](https://github.com/user-attachments/assets/edbb2cb3-0ca5-4afa-bce4-5dff2237c42f)       
this is for the last two characters        
new pw : Flag : jU5t_a_s1mpl3_an4gr4m_4_u_1fb380       

## What I learned :
1. I learnt to analyse code in Java language.
2. Revision of basic looping
3. Revision of functions

## Errors : 
None really, once I figured out the code the steps were pretty basic.

## Resources :
I used ChatGPT to once confirm my new password.







