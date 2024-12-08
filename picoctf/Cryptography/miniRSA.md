# miniRSA

FLAG : picoCTF{n33d_a_lArg3r_e_606ce004}

## Approach
I started by reading the wikipedia page on RSA encryption and I realised that there are three things I'll need
1. N (Public Key Value)
2. e (Public Key)
3. C (Cipher Text)

So I downloaded my source file and did the following
1. I moved my source file called *ciphertext* to my current directory
   ```
   avantikasanyal@LAPTOP-CFRE3HMA:~$ mv /mnt/c/Users/avant/Downloads/ciphertext /home/avantikasanyal/
   ```
2. Then I listed out the files in my currect directory to check if *ciphertext* was in it
   ```
   ls
   ```
3. Then I tried to read the file ciphertext and I got :
   ![image](https://github.com/user-attachments/assets/c0d270a3-d907-4f37-9913-8df554cf4661)

4. Since the file was too big to read, I used *cat*
   ```
   cat ciphertext
   ```

5. And with that, it gave me my C,N and E values
   ![image](https://github.com/user-attachments/assets/61aae2d9-5ce5-4c2b-a3ec-0bd059cbbf35)

6. I went online and found a RSA decoder, and I copied my values from the ciphertext file into the decoder and got my flag.
     ![image](https://github.com/user-attachments/assets/a982760a-5b71-4832-a646-feba01021d73)


## Terminal output
```
avantikasanyal@LAPTOP-CFRE3HMA:~$ mv /mnt/c/Users/avant/Downloads/ciphertext /home/avantikasanyal/
avantikasanyal@LAPTOP-CFRE3HMA:~$ ls /home/avantikasanyal
README.md         ciphertext                     debugger0_a  instructions  key.pub
bandit_notes.txt  cryptonite_taskphase_avantika  flag.txt     key           myflag
avantikasanyal@LAPTOP-CFRE3HMA:~$ file ciphertext
ciphertext: ASCII text, with very long lines (620)
avantikasanyal@LAPTOP-CFRE3HMA:~$ cat ciphertext

N: 29331922499794985782735976045591164936683059380558950386560160105740343201513369939006307531165922708949619162698623675349030430859547825708994708321803705309459438099340427770580064400911431856656901982789948285309956111848686906152664473350940486507451771223435835260168971210087470894448460745593956840586530527915802541450092946574694809584880896601317519794442862977471129319781313161842056501715040555964011899589002863730868679527184420789010551475067862907739054966183120621407246398518098981106431219207697870293412176440482900183550467375190239898455201170831410460483829448603477361305838743852756938687673
e: 3

ciphertext (c): 2205316413931134031074603746928247799030155221252519872649649212867614751848436763801274360463406171277838056821437115883619169702963504606017565783537203207707757768473109845162808575425972525116337319108047893250549462147185741761825125
avantikasanyal@LAPTOP-CFRE3HMA:~$
```

## What did I learn?
RSA (Rivest–Shamir–Adleman) is a public-key cryptosystem, one of the oldest widely used for secure data transmission. The initialism "RSA" comes from the surnames of Ron Rivest, Adi Shamir and Leonard Adleman, who publicly described the algorithm in 1977         

everything I learnt was in the wikipedia page, though I didnt need that much of an in depth understanding considering I got my keys from the file and had to just enter it into an online decoder.

## Errors
None really, I thought this was quite simple.

## Resources
1. https://en.wikipedia.org/wiki/RSA_(cryptosystem)
2. https://www.dcode.fr/rsa-cipher



