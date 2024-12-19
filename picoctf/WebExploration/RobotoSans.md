# Robot Sans

flag : picoCTF{Who_D03sN7_L1k5_90B0T5_032f1c2b}

## My approach :
1. We were again given a link http://saturn.picoctf.net:59329/ and we were told that the flag might not necessarily be on the website. Still, I inspected the website extremely thoroughly to no avail           
![image](https://github.com/user-attachments/assets/f9f0de3e-994b-45dc-9cfc-c9ec4d2ba77a)                                   
2. Then I referred anther repo which had solved
3. I added robots.txt to the original url and got
   ![image](https://github.com/user-attachments/assets/5d3bbdae-5106-4c0f-9a45-7dc076ece4e8)
4. Then I copied each part of the random strings given into CyberChef and tried to decode from Base64 or Hex or URL
5. Finally it worked
   ![image](https://github.com/user-attachments/assets/1a3cd23e-2081-4a90-9fc2-c518c4b15234)
6. Then I appended this js/myfile.txt to the original URL and got my flag
   ![image](https://github.com/user-attachments/assets/46d0d940-40d2-42b4-94dc-e8b089a0ddeb)


## Resources
1. https://github.com/eddiejpagano/picoCTF/blob/45197a03eab850135373ccd8ef181810d2650fe4/WebExploitation/RobotoSans.md
2. ChatGPT

## Errors
I thought inspecting the website would work, but it did not

## What did I learn?
1. *robots.txt* extension
   A robots.txt file tells search engines which parts of your website they can or cannot visit.               
   Use a robots.txt file when:
- Blocking pages you don’t want search engines to crawl (e.g., /admin/, /test/).
- Saving server resources by limiting bot access to unnecessary files or sections.
- Preventing duplicate content issues by blocking duplicate pages (e.g., /print/).
- Hiding unfinished websites like staging or development environments.
- Pointing bots to your sitemap for better indexing (e.g., Sitemap: https://example.com/sitemap.xml).
- Controlling specific bots, like allowing Google but blocking others



