# Day 1

We go to the Glitch's Converter websiter as given, and enter the URL (got RickRolled)                   
Then we download the mp3 files                    
When I open the zip file, I notice that there are two song files
          1. song.mp3
          2. somg.mp3
That is fishy, to say the least.           
On terminal, I use the command 
```
file song.mp3
file somg.mp3
```
We notice that song.mp3 has normal mp3 behaviour, but somg.mp3 is running some powershell command which is not good                

So now we use exiftool                      
*Exiftool- gives us details about audio or image files*                

```
https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1
```
When we check the writeup on this link, we realise that this dude was tryna get out BitCoin. Oh no. WE'd have major losses.                  

Anyways, we realised that this is done by M.M.      

We try to look him up on
```
 https://github.com/search?q=%22Created+by+the+one+and+only+M.M.%22&type=issues
```
And we realise that we had some OPSEC security issues

![image](https://github.com/user-attachments/assets/69e5d1f6-760c-44f2-b5f6-7322727f9061)                 



# Day 2
![image](https://github.com/user-attachments/assets/c7f49745-d007-4087-b851-bc0ccdc721b3)


![image](https://github.com/user-attachments/assets/aa89dc0b-41bf-4dcf-b3d0-dbc7ff8717a8)

appears as if someone is using the generic name *service_admin* to access our system.       
Using source.ip we see that they are using the ip *10.0.11.11*           
we have no idea of the timeline of the attacks, so we look at a different time window to get some idea                        

![image](https://github.com/user-attachments/assets/40a7839a-2dc8-4fa0-9ff0-56c1e38cbffd)                      

wow we had 6k hits            
now lets look at a narrower time                  
now we look at any moves made by the *service_admin* and the *service_admin* only                     

![image](https://github.com/user-attachments/assets/464fccf4-b98b-4dcd-b0b8-f74f3742d912)             

now lets narrow down to that one particular ip we saw                  

![image](https://github.com/user-attachments/assets/f92a8b56-6bcf-401d-853a-ed88ab3cbf57)                     

went down to some 5k hits                          
now filter out the authetication events                              
we notice that the person has consecutively multiple times tried some authentication events, within the span of seconds                    

![image](https://github.com/user-attachments/assets/4e78194d-b68c-4da9-a8a4-1fefb1348e39)                          

a lot of them are failures, but he has succeded too. is this a  *BRUTEFORCE ATTACK*?                   
 ```
Bruteforce attacks - attacks a single acc, tries multiple passwords
```

let's see if there is any other source ip trying to attacks                      

![image](https://github.com/user-attachments/assets/03004722-ee44-49c2-8735-e2ab8217a72c)                      

omg there is *10.0.255.1*                           

![image](https://github.com/user-attachments/assets/9252b906-e0ae-456b-ae2b-149b2be84cb4)                      

this ip has given 1k hits in very lil time span too                              
they did get success with their brute force attack, which isn't good                       
the Glitch has gotten access to our admin acc to use some powershell commands             

What is the said powershell command?         

![image](https://github.com/user-attachments/assets/764d7d78-9730-4718-98bf-debf6594cb0a)                                

decoding the powershell command on CyberChef, we get :                    

![image](https://github.com/user-attachments/assets/7459379e-616a-4ec9-9646-cd9a9cb55449)                      

So the Glitch is pookie, he did brute force attack us, but just to update our systems! 

![image](https://github.com/user-attachments/assets/949e4de0-7f6b-4e09-8c67-222eae688b7b)


# Day 3
![image](https://github.com/user-attachments/assets/132fca86-0056-43d0-a0ef-ee0bc05eccba)       

A file called *shell.php* has been accessed with the parameters c and d.            
And then they are trying to execute some commands.

Example for log analysis :       

![image](https://github.com/user-attachments/assets/0e2b3798-d173-401c-9624-ec0d2ce8702a)   

--------------------------------------------------------------------------------------------------

### File Upload Vunerabilitis
1. RCE - uses HTML, takes an upload, runs a code, then attacker takes control
2. XXE - Uses cookies to imitate you

---------------------------------------------------------------------------------------------------

Reverse shell - starts connection on target
Web shell - just runs on web server

-----------------------------------------------------------------------------------------------------

![image](https://github.com/user-attachments/assets/c3b39d0e-b61b-4180-89a5-292c1ae8f2ac)      

When filtering with this ip, we realise that this ip address was not doing anything malicious              

So, try with the other ip.            

![image](https://github.com/user-attachments/assets/42a98874-6152-407a-a820-ca79ec1881c3)           

Now this dude was trying to run commands - NOT COOL    



![image](https://github.com/user-attachments/assets/9b3fcb54-3bdd-4834-98ba-cded911a56c5)     

10.10.193.232 frostypines.tm    (added this to be able to visit the website)

![image](https://github.com/user-attachments/assets/a2fba828-61c0-4546-89d2-be562dbef7a0)     


# Day 4

1. As usual I started by connecting to the machine.
2. I use this command to see what parameters are available
   ```
   Get-Help Invoke-Atomictest
   ```
   ![image](https://github.com/user-attachments/assets/25d5be34-3068-4aae-97f9-028aa7003972)
3. From the above obtained information we run our first command
   ```
   Invoke-AtomicTest T1566.001 -ShowDetails
   ```

4. This command displays the details of all tests included in the T1566.001 Atomic.
5. We want to run the first test of T1566.001, but before that we must ensure that  all required resources are present.
6. ```
   Invoke-AtomicTest T1566.001 -TestNumbers 1 -CheckPrereq
   ```
7. ![image](https://github.com/user-attachments/assets/406a869d-44dd-4e0d-a85e-7113b672948b)
   This shows how it looks like when all the required pre requisites are present and when some are missing.
8. After that I run the test
   ```
   Invoke-AtomicTest T1566.001 -TestNumbers 1
   ```
  ![image](https://github.com/user-attachments/assets/b2b31781-dc7c-4453-b453-74ab31432699)                     
9. We want log entires for the emulated attack, so we need to first clean up files from the previous test
   ```
Invoke-AtomicTest T1566.001 -TestNumbers 1 -cleanup
```
10. Then we clear the Sysmon Event Log.
    ![image](https://github.com/user-attachments/assets/3eeebb20-3f6a-4178-b645-b3f0cbf5874c)
11. Ran the emulation again
    ```
    Invoke-AtomicTest T1566.001 -TestNumbers 1
    ```
12. In the Operational Log under Event Viewer there should be new events related to the emulated attack
    ![image](https://github.com/user-attachments/assets/eb6f6f54-f1d9-4f76-b643-0755c4b02582)
    (machine died, had to use given ss, sorry)
13. The above details tell us to Navigate to the directory C:\Users\Administrator\AppData\Local\Temp\, and open the file PhishingAttachment.txt
14. Then we cleanup again
    ```
    Invoke-AtomicTest T1566.001-1 -cleanup.
    ```
    ![image](https://github.com/user-attachments/assets/f7f35e19-c9f2-45d6-b882-b4acf1bb4d72)


# Day 5

1. BURP suite is used to intercept requests being made on the website that we want to inspect.
2. We go to this URL on burp site : http://10.10.102.50/product.php.
3. Then we add the Christmas Cap on to the Cart and forward those requests in Burp
4. We proceed to checkout, add our details like name and address
5. We see that once we place our order it says that our's is *wish 21*
6. When we click on Wish 21 it shows that the wishes are only visible to elves
7.  Now, when you visit the URL, http://10.10.102.50/product.php, and click Add to Wishlist, an AJAX call is made to wishlist.php with the following XML as input. 
```
<wishlist>
  <user_id>1</user_id>
     <item>
       <product_id>1</product_id>
     </item>
</wishlist>
```
8. When we review the Add to wishlist request on the burpsuite we can see the request containing the XML part
9. We are updating the XML to:
```
<!DOCTYPE foo [<!ENTITY payload SYSTEM "/etc/hosts"> ]>
<wishlist>
  <user_id>1</user_id>
     <item>
       <product_id>&payload;</product_id>
     </item>
</wishlist>
```
*When we send this updated XML payload, the first two lines introduce an external entity called payload. The line <!ENTITY payload SYSTEM "/etc/hosts"> tells the XML parser to replace the &payload; reference with the contents of the file /etc/hosts on the server. When the XML is processed, instead of a normal product_id, the application will try to load and include the contents of the file specified in the entity*
This show that the payload *is* vulnerable indeed
10. We use the *repeater* option to send multiple post request to exploit vulnerability
11. We update the XML in repeater too
12. On hitting send, the server processed the malicious XML which included an external entity refernce and read the file contents
13. The wishlist.php responded to us by reading the file contents
14. The wishes part was only accessible to admins so we use :
```
<!--?xml version="1.0" ?-->
<!DOCTYPE foo [<!ENTITY payload SYSTEM "/var/www/html/wishes/wish_1.txt"> ]>
<wishlist>
	<user_id>1</user_id>
	<item>
	       <product_id>&payload;</product_id>
	</item>
</wishlist>
```
15. Do the same thing for wish 2 and get your flag 

![image](https://github.com/user-attachments/assets/a9df467e-02ca-461d-9974-8ec93a38d55d)        

![image](https://github.com/user-attachments/assets/ac10d261-c800-4a7b-bd65-b1fe64247081)


![image](https://github.com/user-attachments/assets/33caab46-71fd-4eca-8f3d-e1f472df91b1)

![image](https://github.com/user-attachments/assets/84e080df-0354-42c8-acaa-aff616d47a81)

# Day 6

1. Sandbox - can execute malicious code without worrying about damage to our system
2. YARA - used to identify malware via code
3. We are using YARA to see if it can detect the Malware
4. We cd into tools first
 ```
   FLARE-VM 12/18/2024 19:19:34
PS C:\Users\Administrator > cd C:/
FLARE-VM 12/18/2024 19:19:41
PS C:\ > cd .\Tools\
FLARE-VM 12/18/2024 19:19:46
PS C:\Tools > ls

Directory: C:\Tools

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        10/8/2024   9:14 AM                Explorer Suite
d-----        10/8/2024   9:15 AM                FLOSS
d-----       10/28/2024  10:48 PM                Malware
d-----       10/11/2024   2:38 PM                MinGW
d-----        10/8/2024   9:17 AM                pestudio
d-----        10/8/2024   9:17 AM                Regshot-x64-Unicode
d-----        10/8/2024   9:18 AM                Situational Awareness BOF
d-----        10/8/2024   8:53 AM                SysinternalsSuite
d-----        10/8/2024   9:19 AM                x64dbg
d-----        10/9/2024  12:25 PM                YARARULES
-a----       10/28/2024   9:21 AM           5817 JingleBells.ps1
-a----       12/18/2024   7:03 PM          47904 malstrings.txt
-a----       12/18/2024   6:59 PM           1848 YaraMatches.txt


FLARE-VM 12/18/2024 19:19:50
PS C:\Tools >
```
5. Then we seewhat is in the Jinglebells file
   ```
   Get-Content JingleBells.ps1
   ```
6. Acc to the code we get, it says that if Yara detects anything it will put it in the YaraMatches.txt
7. So to test Yara now we run the powershell - to look for the string constantly
   ```
   .\JingleBells.ps1
   ```
8. Running malware                                  
   ![image](https://github.com/user-attachments/assets/584dc831-7c43-48b1-9f5c-d1e537b3bf6d)
9. The malicious script is MerryChristmas.exe
    ![image](https://github.com/user-attachments/assets/a14763ca-421b-499a-9004-a1396bc9b85e)
10. So we saw that Yara detects for malware by checking for a very specific string
11. Evasion Technique -  to stump Yara, what we do is we use Base64 encoding to convert the identification string so Yara cannot detect it (obsufication)
12. So when we run MerryChristmasObf.exe (contains obfuscated string), Yara doesn't detect the malicious code
13. Floss - optimised for malware analysis, looks for obfuscated techmiques, extracts that and places it in a file for analysis
    ```
    C:\Tools\Malware\MerryChristmas.exe |Out-file C:\tools\malstrings.txt
    ```
    
![image](https://github.com/user-attachments/assets/d42bbc5c-d176-48b9-ab49-2d0485b0b03d)

15. YARA rules can also check Sysmon logs
    ![image](https://github.com/user-attachments/assets/a4649f02-699e-496a-a736-4073d837a402)
16. Here are the multiple sysmon logs we can find (this is a specific process that was created, using it's process id)
    ![image](https://github.com/user-attachments/assets/d4e8afd0-4135-4f9f-ae5b-cbd51ec21b17)
17. This is our specific event
    ![image](https://github.com/user-attachments/assets/1ca1c84d-39b0-4957-879a-10155eac77a6)
![image](https://github.com/user-attachments/assets/05bf0310-d43a-48df-bf3f-c1f40fe905cd)










 























