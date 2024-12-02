# SOAP
flag : picoCTF{XML_3xtern@l_3nt1t1ty_4dbeb2ed}           
Just hit and miss with google and chatgpt and older write-ups (like every other task)             
Also I learnt that shortcuts never work for me and I need to learn and do things from scratch


## My Approach
I simply used inspect and kept pressing random things until I saw this.
![image](https://github.com/user-attachments/assets/07ca607a-2734-4a14-9f70-678daba07b73)
"POST"         
I have vaguely heard of it before.         
Looking up other GitHub repos I learnt that : "Post means I'll have to send a post request which is one of the
HTTP request methods used in web development to send data from a client (usually a web browser or API client like Postman) to a server."     
Okay, so then I downloaded the PostMan app.     
Hint said : XML external entity ejection.         
Now I need to learn how to use postman or send a post request or something.        
THEN IT WAS A STRUGGLE.          
But, I found this website from ApiDog on how to send POST XML with postman and it was given step by step and I just blindly followed it.       

So I learnt that my POST request will have the format
```
<?xml version="1.0" 
encoding="UTF-8"?>
<request>
    <name>John</name>
    <age>18</age>
    <gender>male</gender>
</request>
```
So after following the steps to initiating a post request, I entered the code
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE data [
  
<!ENTITY file SYSTEM "file:///etc/passwd">
]>
<data>
    <ID>&file;</ID>
</data>
```
![image](https://github.com/user-attachments/assets/a10b9936-c642-4273-9aa9-d1b59a5af3b9)

Sweet.       

I also learnt we need to append "data" at the end of the pico saturn link because :                     
The /data part of the link tells the server exactly where you want to send your request. It's like a house address—if you only write
"Main Street" (the base URL), the mailman won't know which house to deliver to. Adding /data is like saying "Main Street, House #5."

Then I sent in my request, and I read through whatever is given and found my flag at the bottom, very cutesy, very mindful.

![image](https://github.com/user-attachments/assets/4691b011-0be6-4cf4-8cdd-53012afcc642)

## What I learned

1. What is a POST?         
   A POST request in the "Network" tab of a website's inspect tools is part of how a browser communicates with a web server. Specifically, a
   POST request is used to send data to the server, often when you're submitting a form, uploading a file, or triggering some kind of action.

2. Why Look at POST in the "Network" Tab?        

The "Network" tab in your browser's developer tools shows all the requests your browser makes to a website, including GET, POST, and others.
When you trigger an action on a site (here it was clicking on 'details' on our page), you might see a POST request appear in the list.
This lets you inspect:
- The URL: Where the data is sent.
- The Headers: Extra info about the request (like content type or authentication tokens).
- The Payload: The actual data being sent (e.g., your login credentials or form inputs).

3. Why Does This Matter?         
 analyzing POST requests can reveal:
- Hidden information about how the website works. (here was our flag hidden)
- Vulnerabilities like injection points (e.g., SQL injection or XXE).
In general, it’s helpful for debugging or understanding how a web app processes data

4. What happens when I send a POST request?         
 -  POST requests send data to the server.
 - They're used for things like submitting forms, logging in, uploading files, or creating new records.
 
Understanding POST requests helps you see where and how data flows, making it
easier to find vulnerabilities or solve challenges. 

5. What is XML?            
   XML (eXtensible Markup Language) is a format used to store and share structured data in a way that both humans and machines can read.
   It looks similar to HTML but is designed to represent data, not web pages. (maybe that is why we appended data at the end?)

   ## References :
   https://apidog.com/articles/how-to-send-post-xml-with-postman/

   ## Errors I made :
   I couldnt send a POST request with our hostel wifi because of security policies, so I had to use mobile data. Not really an error, but
   that did make me redo the thing like 5 times before I realised what could be wrong.







