# m00nwalk2

flag : picoCTF{the_answer_lies_hidden_in_plain_sight}

## My Approach :

The challenge gave us four files - transmission, clue1, clue2 and clue3.     

Putting the clues thru the decoder used for m00nwalk, I got :                

![WhatsApp Image 2024-12-13 at 13 35 17_7d857dbd](https://github.com/user-attachments/assets/b24e95e0-f002-488c-b49a-051bf7493b9d)           

--------------------------------------------------------------------------------------------------------------------------------------------------

### clue 1 
*password* : hidden_stegosaurus
###  clue 2 
the quieter you are, the more you can HEAR
### clue 3
Future Boy

--------------------------------------------------------------------------------------------------------------------------------------------------                          

Looking up Future Boy, I got that it is a steganography tool.             

![image](https://github.com/user-attachments/assets/28602700-c90f-450e-b46f-95a883f2326b)                 

I'll try using Steghide, since it is already downloaded.

```
steghide extract -sf moonwalk2.wav -p hidden_stegosaurus
```

It said that the flag has been copied to some file 

```
cat steganopayload12154.txt
```

And I got my flag!!   


## Terminal Output
```
avantikasanyal@LAPTOP-CFRE3HMA:~$ mv /mnt/c/Users/avant/Downloads/moonwalk2.wav /home/avantikasanyal/
avantikasanyal@LAPTOP-CFRE3HMA:~$ ls
README.md                      custom_decryption.py  encrypted.txt    instructions   newdecrypt.py
atbash.jpg                     customcustom.py       finalcodeman.py  key            thirdcode.py
bandit_notes.txt               debugger0_a           flag.txt         key.pub
ciphertext                     decryption.py         format-string-1  kms.py
convertback.py                 disk.flag.img         help.py          moonwalk2.wav
cryptonite_taskphase_avantika  enc_flag              hex_output.txt   myflag
avantikasanyal@LAPTOP-CFRE3HMA:~$ steghide extract -sf moonwalk2.wav -p hidden_stegosaurus
wrote extracted data to "steganopayload12154.txt".
avantikasanyal@LAPTOP-CFRE3HMA:~$ cat steganopayload12154.txt
picoCTF{the_answer_lies_hidden_in_plain_sight}avantikasanyal@LAPTOP-CFRE3HMA:~$
```

## What I learnt?
nothing new, used knowledge of steghide and moon transmission methods from previous challenges.

## Resources :
1. Steghide
2. Robot36 - SSTV Image Decoder






