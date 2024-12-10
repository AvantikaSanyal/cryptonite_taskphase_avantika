# Custom Encryption

flag : picoCTF{custom_d2cr0pt6d_019c831c}

## My Approach : 

So first I understand the encryption code :
```
from random import randint
import sys


def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    if v > 1:
        return False
    else:
        return True


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def test(plain_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    a = randint(p-10, p)
    b = randint(g-10, g)
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
    cipher = encrypt(semi_cipher, shared_key)
    print(f'cipher is: {cipher}')


if __name__ == "__main__":
    message = sys.argv[1]
    test(message, "trudeau")
```
break it downnnnn
```
def generator(g, x, p):
    return pow(g, x) % p
```
modular exponentiation. It raises g to the power of x, then divides it by p, and returns the remainder             
g = base number, x = secret number, p = prime number

```
def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher
```
plaintext = msg we wanna ecnrpyt, key is key
- It takes each character of the plaintext.
- For each character, it does two things:
                1. It gets the ASCII value of the character using ord(char). For example, ord('A') gives 65.
                2. It multiplies the ASCII value by the key and then by 311 (a constant).
- This process "mixs" the ASCII values and makes the message unreadable

```
def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text
```
This part uses a classic XOR operation. XOR is a bitwise operation that combines two numbers in a special way (don’t worry too much about how it works; the important part is it "scrambles" the character).

```
def test(plain_text, text_key):
    p = 97  # prime number
    g = 31  # base number

    a = randint(p-10, p)  # generate secret number for person A
    b = randint(g-10, g)  # generate secret number for person B

    u = generator(g, a, p)  # public key for person A
    v = generator(g, b, p)  # public key for person B

    key = generator(v, a, p)  # shared secret key for A and B
    b_key = generator(u, b, p)  # another shared secret key to confirm

    if key == b_key:  # If both keys match, use that as the shared key
        shared_key = key
    else:
        print("Invalid key")
        return

    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)  # apply XOR encryption
    cipher = encrypt(semi_cipher, shared_key)  # apply multiplication encryption
    print(f'cipher is: {cipher}')
```
This function combines everything:

1. Key generation:
    - It generates two secret numbers, a and b, for two people (think of them as Alice and Bob).
    - They each use their secret number and the base g and prime p to generate public keys (u and v).
   Using those public keys, they calculate a shared secret key.
2. Message encryption:
    - The function then applies the XOR encryption (dynamic_xor_encrypt) to the plaintext with the text_key (the string "trudeau" in this case).
   After that, it applies the multiplication encryption (encrypt) using the shared secret key.

So the decryption code is :
```
from random import randint

def generator(g, x, p):
    return pow(g, x, p)

def decrypt(cipher, key):
    decrypted_text = ""
    for num in cipher:
        char_code = num // (key * 311)
        decrypted_text += chr(char_code)
    return decrypted_text

def dynamic_xor_decrypt(cipher_text, text_key):
    decrypted_text = ""
    key_length = len(text_key)
    for i, char in enumerate(cipher_text):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        decrypted_text += decrypted_char
    return decrypted_text[::-1]

def decode(cipher, a, b, g=31, p=97, text_key="trudeau"):
    u = generator(g, a, p)
    v = generator(g, b, p)
    shared_key = generator(v, a, p)
    semi_cipher = decrypt(cipher, shared_key)
    plaintext = dynamic_xor_decrypt(semi_cipher, text_key)
    return plaintext

ciphered_message = [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470, 936110, 10885, 674870, 261240, 293895, 65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045] 
a = 88
b = 26
decoded_message = decode(ciphered_message, a, b)
print("Decoded message:", decoded_message)
```
now we have to use the contents of enc_flag as the input for the decryption code
```
avantikasanyal@LAPTOP-CFRE3HMA:~$ mv /mnt/c/Users/avant/Downloads/kms.py /home/avantikasanyal/
avantikasanyal@LAPTOP-CFRE3HMA:~$ cat enc_flag | python3 kms.py
```
AND WE HAVE FLAG 

## Terminal Output

```
avantikasanyal@LAPTOP-CFRE3HMA:~$ cat enc_flag
a = 88
b = 26
cipher is: [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470, 936110, 10885, 674870, 261240, 293895, 65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045]
avantikasanyal@LAPTOP-CFRE3HMA:~$ cat enc_flag | python3 kms.py
python3: can't open file '/home/avantikasanyal/kms.py': [Errno 2] No such file or directory
avantikasanyal@LAPTOP-CFRE3HMA:~$ mv /mnt/c/Users/avant/Downloads/kms.py /home/avantikasanyal/
avantikasanyal@LAPTOP-CFRE3HMA:~$ cat enc_flag | python3 kms.py
Decoded message: picoCTF{custom_d2cr0pt6d_019c831c}
```


## What I learnt?
XOR encryption





