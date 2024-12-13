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























