# tunn3l_v1s10n

flag : picoCTF{qu1t3_a_v13w_2020}

THIS ONE TESTED MY PATIENCE I WAS SO SO CLOSE TO YEETING MY LAPTOP INTO OBLIVION

# My Approach

I poked around on GitHub and I saw that this challenge is related to hvaing to change some hexadecimal values.       
Off I went to ChatGPT to find out what I can do

1. I went to a hex editor website and opened my downloaded file there.
               
   ![image](https://github.com/user-attachments/assets/658123ab-1ff1-4b5b-86d3-47bd0485709f)              
   This is what I saw.

2. ChatGPT told me that for a *.bmp* file, the file header should look like (Why *.bmp*? Well, we used this before for something and also a secret code is in an image which is what we do with .bmp files)
   ```
   42 4D C6 94 0C 00 00 00 00 00 36 00 00 00 28 00
   ```

3. Clearly, mine didn't match, so I changed as required
   
   ![image](https://github.com/user-attachments/assets/45206c8d-5864-4652-95bc-ecf70a596bbe)

4. Then I saved the file, and I tried opening it normally and I see
   
   ![image](https://github.com/user-attachments/assets/ad423967-164d-4756-bcf9-1e06126a5c96)

5. *cue me maniacally screaming because I was already frustrated with this challenge* " WHY AM I NOT GETTING THE FULL IMAGE WHAT IS WRONG I WANT FULL- oh"           
  
6.  I realised I might have to change the dimensions of the file. Off we go to ChatGPT again.

7.  I change a few dimensions on the same hexeditor thing
```
- Look for the 22nd byte (offset 0x16).
- You will see the current height stored as 32 01 00 00 (little-endian format for 0132).
- Modify the Height
- Replace 32 01 00 00 (current height) with 52 03 00 00:
- 850 in decimal is 0352 in hexadecimal.
- Write it in little-endian format: 52 03 00 00.
```

![image](https://github.com/user-attachments/assets/a1fae397-af34-45bc-829f-b3bd9568bcf8)            

8. After changing the value, I got this image        
   
   ![image](https://github.com/user-attachments/assets/05402c57-3b26-4701-b374-439967140f08)   



   ## What I learnt

   1. Digital images, like most files, are represented as binary data, and this data can be displayed in hexadecimal (base-16) format for analysis and editing
   2. I learnt what the file header for a *.bmp* file should look like
   3. I learnt how to change the size of an image in its hexadecimal form
   4. Patience
  
   ## Errors
   1. I got stuck so many times as ChatGPT kept leading me astray. It tried to get me to download a bunch of apps
   2. Faced lots of problems with the location of my files
   3. I tried using Ubuntu for this, clearly didn't need it
  
   ## Resources
   https://hexed.it/






