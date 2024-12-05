# Trivial Flag Transfer Protocol

Flag : picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}       
This was THE HARDEST one I have done so far, and I'll be honest, I just used another friend's repo for this because I had absolutely not the slightest clue 
as to what I should do. But, I will describe every step in intricate detail to prove I learnt and understood what I did.

## Approach :
1. First I downloaded the file. It was of format pcapng whis is : A .pcapng file (Packet Capture Next Generation) is a network packet capture file, commonly used to analyze network traffic.
   
2. A quick google tells me that apps like WireShark are used for these type of files.
   
3. I also used the following commands just to poke around my file a little :
   ![image](https://github.com/user-attachments/assets/bad21463-5df9-40c8-b14c-e55122a75174)       
   I do not think this step was needed but the repo I was referring to had it, so I went ahead.         
   *note : If your file is located at          
    C:\Users\avant\Downloads\tftp (1).pcapng
   and you're working in a Linux-based environment (like WSL), you need to use the Linux path for the file.*        

*In WSL, Windows files under C:\ are mounted under /mnt/c/.*
*So final code :*
```
/mnt/c/Users/avant/Downloads/tftp\ \(1\).pcapng
```
   

4. Install WireShark for Windows.
   
5. Then I uploaded the pcapng file unto wireshark and got this :   

![image](https://github.com/user-attachments/assets/4ccd510a-5a39-45aa-aaaa-cde8222235e6)     

6. Then in the filter bar, I entered *tftp.type* and I get :      
 
![image](https://github.com/user-attachments/assets/4324cf12-cf62-4d52-bbdb-65b7c9da1fd3)                 

*note : The tftp.type filter in Wireshark is used to filter packets based on the specific TFTP (Trivial File Transfer Protocol) operation types.*                
I am assuming these two steps were to understand what is in our pcapng file.

7. Then I opened the pcapng file and saw two specific files called *instructions* and *plan*. They looked clearly encrypted. So I Rot13 both :

instructions file :            
![image](https://github.com/user-attachments/assets/f6995cea-a043-4abc-a8cc-a48fb2a91a70)   

plan file :           
![image](https://github.com/user-attachments/assets/b6114f60-cbe5-4479-9344-24697a78f20d)

8. Spacing out both the decrypted messages I get :       
       *TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN*       
     It mentions "plan", our plan file says         
       *I USED THE PROGRAM AND HID IT WITH-DUE DILIGENCE. CHECKOUT THE PHOTOS*         

9. Now I opened the pcapng file and got the following images.            
 ![image](https://github.com/user-attachments/assets/599ec9f4-abbb-467b-8a0b-94e71e5708d5)
 ![image](https://github.com/user-attachments/assets/985eb94e-8767-4fb7-a504-41e192d0ecd6)
 ![image](https://github.com/user-attachments/assets/c801b7a7-fe5a-47fe-909b-246ee645669d)       

10. Now, these are just screenshots of images. I noted that they had a .bmp extension.            
    *The .bmp file extension stands for Bitmap Image File, a widely used raster graphics file format that stores bitmap digital images. The format is
    known for its simplicity and compatibility with almost all image viewers and editors.*
    
   *One of the Key Characteristics of .bmp Files is that :            
BMP files are usually uncompressed, meaning they store every pixel of an image. This leads to larger file sizes compared to formats like JPEG or PNG.*
*Because of this uncompressed format, they are used in Uses of .bmp Files         
Steganography: Due to the uncompressed nature of BMP files, they are often used in steganography tools like Steghide for hiding secret data.*

12. So now I download steghide.                 
        *Steghide is a command-line tool used for steganography, the practice of hiding information within other non-secret files, such as images or audio files. It is often used to embed secret messages or files into ordinary media files without changing their visual or auditory quality significantly.*

13. After that, I update my Linux package using :
```
sudo apt update
```

13. Then I install steghide           
    ```
    sudo apt install steghide
    ```

14. After installation, I use the steghide extract command           
    ```
    steghide extract -sf <carrier_file>
    ```
    *The steghide extract -sf command is used to extract hidden data (e.g., a file or message) from a carrier file (such as an image or audio file) in which data was previously embedded using Steghide.*

15. I individually extract each image and use the pass key *DUEDILIGENCE* as given in the "plan" file.
    ![image](https://github.com/user-attachments/assets/186b059f-aaee-41ee-899d-582a853a9615)
    Nothing could be extracted from the first two files, but steghide copies my flag from the third picture into a file called "flag.txt.

16. I read the flag file
    ```
    cat flag.txt
    ```
    It gives me my flag.
    ![image](https://github.com/user-attachments/assets/755e82a8-984c-42f1-b3be-a73856bb38d8)

    ## Terminal Output :
    ```
    avantikasanyal@LAPTOP-CFRE3HMA:~$ file /mnt/c/Users/avant/Downloads/tftp\ \(1\).pcapng
    /mnt/c/Users/avant/Downloads/tftp (1).pcapng: pcapng capture file - version 1.0
    avantikasanyal@LAPTOP-CFRE3HMA:~$ hexdump -C /mnt/c/Users/avant/Downloads/tftp\ \(1\).pcapng | head
    00000000  0a 0d 0d 0a b8 00 00 00  4d 3c 2b 1a 01 00 00 00  |........M<+.....|
    00000010  ff ff ff ff ff ff ff ff  02 00 36 00 49 6e 74 65  |..........6.Inte|
    00000020  6c 28 52 29 20 43 6f 72  65 28 54 4d 29 20 69 37  |l(R) Core(TM) i7|
    00000030  2d 38 35 35 30 55 20 43  50 55 20 40 20 31 2e 38  |-8550U CPU @ 1.8|
    00000040  30 47 48 7a 20 28 77 69  74 68 20 53 53 45 34 2e  |0GHz (with SSE4.|
    00000050  32 29 00 00 03 00 17 00  4c 69 6e 75 78 20 35 2e  |2)......Linux 5.|
    00000060  37 2e 30 2d 6b 61 6c 69  31 2d 61 6d 64 36 34 00  |7.0-kali1-amd64.|
    00000070  04 00 3a 00 44 75 6d 70  63 61 70 20 28 57 69 72  |..:.Dumpcap (Wir|
    00000080  65 73 68 61 72 6b 29 20  33 2e 32 2e 35 20 28 47  |eshark) 3.2.5 (G|
    00000090  69 74 20 76 33 2e 32 2e  35 20 70 61 63 6b 61 67  |it v3.2.5 packag|
    avantikasanyal@LAPTOP-CFRE3HMA:~$ wireshark /mnt/c/Users/avant/Downloads/tftp\ \(1\).pcapng
    Command 'wireshark' not found, but can be installed with:
    sudo apt install wireshark-qt
    avantikasanyal@LAPTOP-CFRE3HMA:~$ sudo apt install steghide
    [sudo] password for avantikasanyal:
     Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    E: Unable to locate package steghide
    avantikasanyal@LAPTOP-CFRE3HMA:~$ steghide extract -sf /mnt/c/Users/avant/Downloads/picture1
    Command 'steghide' not found, but can be installed with:
    sudo apt install steghide
    avantikasanyal@LAPTOP-CFRE3HMA:~$ sudo apt install steghide
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    E: Unable to locate package steghide
    avantikasanyal@LAPTOP-CFRE3HMA:~$ steghide extract -sf /mnt/c/Users/avant/Downloads/picture1.bmp
    Command 'steghide' not found, but can be installed with:
    sudo apt install steghide
    avantikasanyal@LAPTOP-CFRE3HMA:~$ sudo apt update
    Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
    Get:2 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [128 kB]
    Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [129 kB]
    Get:4 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [1956 kB]
    Get:5 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [127 kB]
    Get:6 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages [14.1 MB]
    Get:7 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [313 kB]
    Get:8 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [13.3 kB]
    Get:9 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [2611 kB]
    Get:10 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [453 kB]
    Get:11 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 c-n-f Metadata [580 B]
    Get:12 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [958 kB]
    Get:13 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [203 kB]
    Get:14 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [19.5 kB]
    Get:15 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 Packages [37.6 kB]
    Get:16 http://security.ubuntu.com/ubuntu jammy-security/multiverse Translation-en [8260 B]
    Get:17 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 c-n-f Metadata [224 B]
    Get:18 http://archive.ubuntu.com/ubuntu jammy/universe Translation-en [5652 kB]
    Get:19 http://archive.ubuntu.com/ubuntu jammy/universe amd64 c-n-f Metadata [286 kB]
    Get:20 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages [217 kB]
    Get:21 http://archive.ubuntu.com/ubuntu jammy/multiverse Translation-en [112 kB]
    Get:22 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 c-n-f Metadata [8372 B]
    Get:23 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [2180 kB]
    Get:24 http://archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [372 kB]
    Get:25 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [17.9 kB]
    Get:26 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [2705 kB]
    Get:27 http://archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [470 kB]
    Get:28 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [612 B]
    Get:29 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [1178 kB]
    Get:30 http://archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [287 kB]
    Get:31 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [26.4 kB]
    Get:32 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [44.5 kB]
    Get:33 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse Translation-en [11.5 kB]
    Get:34 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [440 B]
    Get:35 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 Packages [67.7 kB]
    Get:36 http://archive.ubuntu.com/ubuntu jammy-backports/main Translation-en [11.1 kB]
    Get:37 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 c-n-f Metadata [388 B]
    Get:38 http://archive.ubuntu.com/ubuntu jammy-backports/restricted amd64 c-n-f Metadata [116 B]
    Get:39 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [28.9 kB]
    Get:40 http://archive.ubuntu.com/ubuntu jammy-backports/universe Translation-en [16.5 kB]
    Get:41 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 c-n-f Metadata [672 B]
    Get:42 http://archive.ubuntu.com/ubuntu jammy-backports/multiverse amd64 c-n-f Metadata [116 B]
    Fetched 34.7 MB in 1min 1s (567 kB/s)
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    135 packages can be upgraded. Run 'apt list --upgradable' to see them.
    avantikasanyal@LAPTOP-CFRE3HMA:~$ sudo apt install steghide
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    The following additional packages will be installed:
     libjpeg-turbo8 libjpeg8 libmcrypt4 libmhash2
    Suggested packages:
     libmcrypt-dev mcrypt
    The following NEW packages will be installed:
      libjpeg-turbo8 libjpeg8 libmcrypt4 libmhash2 steghide
    0 upgraded, 5 newly installed, 0 to remove and 135 not upgraded.
    Need to get 445 kB of archives.
    After this operation, 1469 kB of additional disk space will be used.
    Do you want to continue? [Y/n] Y
    Get:1 http://archive.ubuntu.com/ubuntu jammy/main amd64 libjpeg-turbo8 amd64 2.1.2-0ubuntu1 [134 kB]
    Get:2 http://archive.ubuntu.com/ubuntu jammy/main amd64 libjpeg8 amd64 8c-2ubuntu10 [2264 B]
    Get:3 http://archive.ubuntu.com/ubuntu jammy/universe amd64 libmcrypt4 amd64 2.5.8-7 [68.8 kB]
    Get:4 http://archive.ubuntu.com/ubuntu jammy/main amd64 libmhash2 amd64 0.9.9.9-9build2 [95.9 kB]
    Get:5 http://archive.ubuntu.com/ubuntu jammy/universe amd64 steghide amd64 0.5.1-15 [144 kB]
    Fetched 445 kB in 4s (104 kB/s)
    Selecting previously unselected package libjpeg-turbo8:amd64.
    (Reading database ... 24208 files and directories currently installed.)
    Preparing to unpack .../libjpeg-turbo8_2.1.2-0ubuntu1_amd64.deb ...
    Unpacking libjpeg-turbo8:amd64 (2.1.2-0ubuntu1) ...
    Selecting previously unselected package libjpeg8:amd64.
    Preparing to unpack .../libjpeg8_8c-2ubuntu10_amd64.deb ...
    Unpacking libjpeg8:amd64 (8c-2ubuntu10) ...
    Selecting previously unselected package libmcrypt4.
    Preparing to unpack .../libmcrypt4_2.5.8-7_amd64.deb ...
    Unpacking libmcrypt4 (2.5.8-7) ...
    Selecting previously unselected package libmhash2:amd64.
    Preparing to unpack .../libmhash2_0.9.9.9-9build2_amd64.deb ...
    Unpacking libmhash2:amd64 (0.9.9.9-9build2) ...
    Selecting previously unselected package steghide.
    Preparing to unpack .../steghide_0.5.1-15_amd64.deb ...
    Unpacking steghide (0.5.1-15) ...
    Setting up libjpeg-turbo8:amd64 (2.1.2-0ubuntu1) ...
    Setting up libmhash2:amd64 (0.9.9.9-9build2) ...
    Setting up libmcrypt4 (2.5.8-7) ...
    Setting up libjpeg8:amd64 (8c-2ubuntu10) ...
    Setting up steghide (0.5.1-15) ...
    Processing triggers for man-db (2.10.2-1) ...
    Processing triggers for libc-bin (2.35-0ubuntu3.4) ...
    avantikasanyal@LAPTOP-CFRE3HMA:~$ steghide extract -sf /mnt/c/Users/avant/Downloads/picture1.bmp
    Enter passphrase:
    steghide: could not extract any data with that passphrase!
    avantikasanyal@LAPTOP-CFRE3HMA:~$ steghide extract -sf /mnt/c/Users/avant/Downloads/picture2.bmp
    Enter passphrase:
    steghide: could not extract any data with that passphrase!
    avantikasanyal@LAPTOP-CFRE3HMA:~$ steghide extract -sf /mnt/c/Users/avant/Downloads/picture3.bmp
    Enter passphrase:
    wrote extracted data to "flag.txt".
     avantikasanyal@LAPTOP-CFRE3HMA:~$ cat flag.txt
     picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
     avantikasanyal@LAPTOP-CFRE3HMA:~$
   ```
```
## What did I learn :

1. What is wireshark and how to use it?
2. What is Steganography?
3. How to use Steghide for steganography1/
4. How to update Linux Packages

## References :
1. ChatGPT
2. https://rot13.com/
3. https://sourceforge.net/projects/steghide/
4. https://www.wireshark.org/

## Errors I made :
1. I was calling the pcapng wrong. I needed to use /mnt/c ahead of it
2. I downloaded steghide but tried to use it without updating my Linux Package.







    



