# vault door 5

flag :picoCTF{c0nv3rt1ng_fr0m_ba5e_64_0b957c4f}

## My Approach : 
I read the challenge which said : *this vault door uses a different change of base as well as URL encoding!*                
So I figured I would have to use Base64 decoder and a URL decoder.                            
I put the given code thru ChatGPT :
```
import java.net.URLDecoder;
import java.util.*;

class VaultDoor5 {
    public static void main(String args[]) {
        VaultDoor5 vaultDoor = new VaultDoor5();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTMwJTYyJTM5JTM1JTM3JTYzJTM0JTY2";
        return base64Encoded.equals(expected);
    }
}
```
and the ChatGPT gave me the following code in Python which decodes from Base64 then URL :
```
import base64
from urllib.parse import unquote

# Expected Base64 encoded string
encoded_string = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTMwJTYyJTM5JTM1JTM3JTYzJTM0JTY2"

# Step 1: Base64 decode
decoded_base64 = base64.b64decode(encoded_string).decode()

# Step 2: URL decode
decoded_url = unquote(decoded_base64)

# The result is the original password
print(decoded_url)
```
I ran this code and got my flag : ![image](https://github.com/user-attachments/assets/d21767fe-fea1-4df4-9c13-efcef37d5bfe)                           

## Errors
I tried using online decoders but that wasn't working for some reason

## Resources
ChatGPT

## What did I learn?
Reused the concept of Base64 and URL encoding/decoding
