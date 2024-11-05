# ARMssembly 1
flag : picoCTF{00000d2a}  

## My Approach
I opened the code that they gave us in VScode and I was like wtf because this was the first time I saw assembly language

So what now? Reading the challenge description, I saw that they were asking me to find for what argument do I get a certain output, This kinda 
reminds me of what we're learning in C right now where we have to calculate what output we're getting from certain code snippet.
However, I do not know Assembly Language, so I put this code through ChatGPT asking it to explain to me what exactly is happening here.

And this is what I figured out:  

1. We have a function called func
2. We have some constants defined for which we need to see what value func returns.
3. 79 (stored at [sp, 16])
   7 (stored at [sp, 20])
   3 (stored at [sp, 24])
4. Now we perform the operations in func
   
    ### left shift operations:
   ```
   ldr	w0, [sp, 20]
	ldr	w1, [sp, 16]
	lsl	w0, w1, w0
	str	w0, [sp, 28]
   ```
 -  first we load 7 to w0 and 79 to w1  
 -  In the next step with lsl what we're doing is 79<<7 = 10112  
(79 in binary: 1001111.  
Shift it left by 7 bits: 10011110000000.  
Convert 10011110000000 back to decimal)  
  -  Then we stored this 10112 in [sp,28]  
  
  ### division operations:
   ```
   ldr	w1, [sp, 28]
	ldr	w0, [sp, 24]
	sdiv	w0, w1, w0
	str	w0, [sp, 28]
   ```
  - so here we are  loading 10112 into w1 and 3 into  w0 (like initialising variables)  
  - Then with sdiv we divide 10112/3= 3370  
  - store this 3370 at [sp,28]  

  ### subtraction operations:  
  ```
  ldr	w1, [sp, 28]
	ldr	w0, [sp, 12]
	sub	w0, w1, w0
	str	w0, [sp, 28]
```
- now we load whatever is at [sp,28] which is 3370 into w1.  
- and the originial input at w0.  
- the sub command  subtracts this input from 3370. THIS IS OUR CRUCIAL POINT!!!!!  
- then wee store our result at [sp,28]    

### returning  value:
```
ldr	w0, [sp, 28]
```
- we are loading the final result from [sp,28] to w0 to return it  
- then we use "ret" to return it

 5. okay so now i come down to the eqn 
```
3370-input=0
```
So the value being returned to me is 3370  

6. Now we convert 3370 to hexadecimal
   which is 0d2a  
   
7. The flag format specifies that the hexadecimal value should be 32 bits long. In hexadecimal, a 32-bit number should have 8 characters.
   So we do "padding" where we simply add leading 0s.
   
9. Then I put it in the flag format.  


## Terminal Output:

![ARMssemble1 ss1](https://github.com/user-attachments/assets/6f5bec04-bd63-4983-92ba-bd95fc4fa3ae)

![ARMssembly1 ss2](https://github.com/user-attachments/assets/5b82173f-9fe4-43dc-8e0b-c06560052bf0)


## What I learned?
   
   I learnt some Assembly commands.
   1. sub sp, sp, #32 : allocates 32 bytes on stack
   2. str : stores input argument at certain offset location on the stack
   3. mov : loads some value onto some register variable
   4. ldr : loads value from offset to register
   5. lsl : left shift
   6. str : stores result on stack again
   7. sdiv : simple division
   8. sub : subtracts
   9. add : restore stack pointer to its prev position
   10. ret : retrun from function

       also I learnt:
       What is a stack?
       
           A stack is a linear data structure that follows the LIFO (Last-In-First-Out) principle.
           This means that the last element added to the stack is the first one to be removed.
       What is a register?
       
            High-speed storage locations within the CPU. 
            Used to store data temporarily during calculations, program execution, and data transfers.
       What is an offset?
       
            A numerical value added to a base address to locate a specific memory location.
            Used to access data within a larger data structure, like an array or a block of memory.

       ## References
       1. ChatPT   
       2. Gemini   
       3. https://www.allaboutcircuits.com/technical-articles/how-to-write-assembly-basic-assembly-instructions-ARM-instruction-set/


