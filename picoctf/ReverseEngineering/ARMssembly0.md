# ARMssembly 0

flag : picoCTF{f51e846f}

## My Approach :
I used a website and converted the given code in assembly language to C.              
Given code in assembly :
```
	.arch armv8-a
	.file	"chall.c"
	.text
	.align	2
	.global	func1
	.type	func1, %function
func1:
	sub	sp, sp, #16
	str	w0, [sp, 12]
	str	w1, [sp, 8]
	ldr	w1, [sp, 12]
	ldr	w0, [sp, 8]
	cmp	w1, w0
	bls	.L2
	ldr	w0, [sp, 12]
	b	.L3
.L2:
	ldr	w0, [sp, 8]
.L3:
	add	sp, sp, 16
	ret
	.size	func1, .-func1
	.section	.rodata
	.align	3
.LC0:
	.string	"Result: %ld\n"
	.text
	.align	2
	.global	main
	.type	main, %function
main:
	stp	x29, x30, [sp, -48]!
	add	x29, sp, 0
	str	x19, [sp, 16]
	str	w0, [x29, 44]
	str	x1, [x29, 32]
	ldr	x0, [x29, 32]
	add	x0, x0, 8
	ldr	x0, [x0]
	bl	atoi
	mov	w19, w0
	ldr	x0, [x29, 32]
	add	x0, x0, 16
	ldr	x0, [x0]
	bl	atoi
	mov	w1, w0
	mov	w0, w19
	bl	func1
	mov	w1, w0
	adrp	x0, .LC0
	add	x0, x0, :lo12:.LC0
	bl	printf
	mov	w0, 0
	ldr	x19, [sp, 16]
	ldp	x29, x30, [sp], 48
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
	.section	.note.GNU-stack,"",@progbits
```
Converted code in Python :
```
import sys

def func1(a, b):
    if b <= a:
        return a
    return b

def main():
    if len(sys.argv) < 3:
        print("Usage: python script.py <num1> <num2>")
        return

    num1 = int(sys.argv[1])
    num2 = int(sys.argv[2])
    
    result = func1(num1, num2)
    print(f"Result: {result}")

if __name__ == "__main__":
    main()

```
When we analyse the Python code, we realise that the code returns the greater of the two inputs.                                           
The two inputs according to the challenge are : 4112417903 and 1169092511                                    
Hence the output is : 4112417903.                         
Convert it to hex and our flag is picoCTF{f51e846f}

## Errors 
Made some errors while converting to hex

## Resources 
https://www.codeconvert.ai/assembly-to-python-converter
ChatGPT

## What did I learn?
1. Conversion to Hex
2. Analysing a Python code
