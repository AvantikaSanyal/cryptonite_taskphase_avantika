# Hide To See

flag : picoCTF{atbash_crack_92533667}

## My Approach :
![image](https://github.com/user-attachments/assets/db306123-26e8-42c3-87ca-80f2b030369d)                             

This involves some *hide and seek*. Hmmm, a picture, and hide? Let's use, steghide.

```
steghide extract -sf atbash.jpg
```
What's the passphrase?        
No idea, I simply pressed enter.     

Then it said that it has copied the file to 'encypted.txt".        
```
cat encrypted.txt
```
I got : krxlXGU{zgyzhs_xizxp_92533667}.                      

Correspond the letters in the above text to the image, it's like a key. 

And you get the flag!!!
