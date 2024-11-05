# COOKIES

Hiii, so absolutely excited that this was my first Pico challenge that I did on my own (lil help from ChatGPT :D )

  flag : picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd}

  ### My Approach:  
  
  So I chose this challenge as my first one because in the OASIS CTF we had a similar challenge where we had to do what I learnt is "fuzz testing",
  "cookie manipulation" or even "cookie fuzzing".
  So I went to the link given, and in their home page I entered "snickerdoodles" like it was prompted in the text area. I was taken to a 
  page which kept talking about how it liked some specific type of cookie.
Anyway, following what I did in OASIS, I went to the page inspect, Applications, Cookies. I saw this had a value of 0. So I changed it to 1 (as 
that worked in my CTF). I saw that on reloading my page, the type of cookie that the page said it liked changed (THATS HOW DIFFERENT DATA AFFECTS 
THE WEBSITES!!!). So I went in blindly and I kept changing the value and reloading the page a billion times :D
After 17 tries, when I entered 18, it gave me my wonderful flag.

### Terminal Output:  

My terminal output was :


![image](https://github.com/user-attachments/assets/8cc9bcde-879e-411c-9ad7-0cfb274c036e)

### What I learned?  


1. COOKIE MANIPULATION  
   Cookie Manipulation is done basically to see how an application or website responds to different cookie values. This helps reveal
   any vulnerabilities or secret functionalities that may be in the website.

   Why we do this?  
   i) to test application logic
   ii) changing the cookie values can give us access to other controls or contents
   iii) to expose any flaws

2. What even is a cookie?  
   Invented in 1994.
   Not the diabetes bombs, a website cookie , or HTTP cookie, is a small piece of data from a users website stored while browsing said web.
   
3.What does a cookie do?  
   Store your browser activity for maybe giving you targeted ads or storing your login and password. Website owners use cookies to count how 
   many users are going to their website.

4. How does a cookie work?  
   When I visit a website for the first time, the website puts a cookie with a unique ID for me on my hard drive. The site then uses this
   ID to track me (THIS COULD BE A BREACH OF PRIVACY BUT OK)
   


   ### Incorrect methods
   
   None really for this, I just kept doing hit and trial method to check which cookie value would work. I started from -1 to 18.

   ### References
   
   1. https://www.youtube.com/watch?v=rdVPflECed8 (what tf is a cookie?)
   2. ChatGPT for cookie manipulation info
      
   

  


