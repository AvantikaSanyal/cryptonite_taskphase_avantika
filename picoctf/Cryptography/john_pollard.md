# john_pollard

flag : picoCTF{73176001,67867967}

## Hints
1. The flag is in the format picoCTF{p,q}
2. Try swapping p and q if it does not work

## My Approach :

challenge desc : *Sometimes RSA certificates are breakable*        

What does a RSA certificate even mean? I look up *RSA certificate decoder* amd get a website which directly asks me to enter the certificate given in the file from the challenge. Sweet!!         

![image](https://github.com/user-attachments/assets/bd4715cc-f1ea-4fb4-beaf-55b9d8f53f4c)                 

So I enter my certificate into the website like so :       
![image](https://github.com/user-attachments/assets/79a0a18f-5575-4131-bc23-0983bd9d541a)                       

So I scroll down and see the plethora of information that they have provided to me....           
![image](https://github.com/user-attachments/assets/a1f6bd29-1afa-4be9-ae32-85c243000a1d)              

I have no clue what's happening but then I come across familiar words - *public key, modulus and exponent*          

I go back to the concept of RSA and I see that  :      
            ![image](https://github.com/user-attachments/assets/bce3be69-8c3e-4cc9-bc29-05bcb3c88328)        

Wait, it is starting to make sense, according to the clue they have said the flag is *p,q*, modulus = p*q and our certificate decoder gave us modulus!!!!!             
So, now I need to factorise modulus (I use a random online calculator for this)           
![image](https://github.com/user-attachments/assets/7a32efbf-918c-4a42-b01e-6513a23f4f13)                    
Flag achieved!!!

## Terminal Output
```
avantikasanyal@LAPTOP-CFRE3HMA:~$ cd /mnt/c/Users/avant/Downloads
avantikasanyal@LAPTOP-CFRE3HMA:/mnt/c/Users/avant/Downloads$ cat cert
-----BEGIN CERTIFICATE-----
MIIB6zCB1AICMDkwDQYJKoZIhvcNAQECBQAwEjEQMA4GA1UEAxMHUGljb0NURjAe
Fw0xOTA3MDgwNzIxMThaFw0xOTA2MjYxNzM0MzhaMGcxEDAOBgNVBAsTB1BpY29D
VEYxEDAOBgNVBAoTB1BpY29DVEYxEDAOBgNVBAcTB1BpY29DVEYxEDAOBgNVBAgT
B1BpY29DVEYxCzAJBgNVBAYTAlVTMRAwDgYDVQQDEwdQaWNvQ1RGMCIwDQYJKoZI
hvcNAQEBBQADEQAwDgIHEaTUUhKxfwIDAQABMA0GCSqGSIb3DQEBAgUAA4IBAQAH
al1hMsGeBb3rd/Oq+7uDguueopOvDC864hrpdGubgtjv/hrIsph7FtxM2B4rkkyA
eIV708y31HIplCLruxFdspqvfGvLsCynkYfsY70i6I/dOA6l4Qq/NdmkPDx7edqO
T/zK4jhnRafebqJucXFH8Ak+G6ASNRWhKfFZJTWj5CoyTMIutLU9lDiTXng3rDU1
BhXg04ei1jvAf0UrtpeOA6jUyeCLaKDFRbrOm35xI79r28yO8ng1UAzTRclvkORt
b8LMxw7e+vdIntBGqf7T25PLn/MycGPPvNXyIsTzvvY/MXXJHnAqpI5DlqwzbRHz
q16/S1WLvzg4PsElmv1f
-----END CERTIFICATE-----
avantikasanyal@LAPTOP-CFRE3HMA:/mnt/c/Users/avant/Downloads$
```

## What did I learn
RSA certificate

## Errors
None really, this was direct and everything was available on the internet

## Resources
1. https://certlogik.com/decoder/
2. https://factordb.com/index.php?query=4966306421059967
3. https://chatgpt.com/c/6774f879-8ef0-800c-9043-bf2ee4cff493
   






