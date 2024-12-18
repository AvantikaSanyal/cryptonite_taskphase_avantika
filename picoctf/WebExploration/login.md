# Login

flag : picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}

## My Approach

1. I went to the given link : login.mars.picoctf.net
2. It took me to a login page as expected                                      
   ![image](https://github.com/user-attachments/assets/af67640f-d099-4126-a0fe-09b47b5c47c9)
3. Then because there were no hints or no other description, I simply inspected the page
4. Under Sources, there was a script called *index.js*
   ![image](https://github.com/user-attachments/assets/6ba7cc7b-d3d5-480a-a6e5-e47f21ec2915)
5. The code was
   ```
   (async () => {
    await new Promise((e => window.addEventListener("load", e))),
    document.querySelector("form").addEventListener("submit", (e => {
        e.preventDefault();
        const r = {
            u: "input[name=username]",
            p: "input[name=password]"
        }
          , t = {};
        for (const e in r)
            t[e] = btoa(document.querySelector(r[e]).value).replace(/=/g, "");
        return "YWRtaW4" !== t.u ? alert("Incorrect Username") : "cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ" !== t.p ? alert("Incorrect Password") : void alert(`Correct Password! Your flag is ${atob(t.p)}.`)
    }
   ```
6. The code talks about username and password and has two elements that do not look like regular code 
       *"YWRtaW4" AND "cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ"*
7. I put this code into ChatGPT and asked it to identify a password and username
8. I got a return saying that the two abnormal values were in Base64V and after decoding
   ![image](https://github.com/user-attachments/assets/b1493843-c173-4154-93dc-daad1f849e7a)              

## Errors
none really, pretty simple

## Resources
ChatGPT

## What did I learn?
Reading a .js script

