# Easy1

## Challenge
The one time pad can be cryptographically secure, but not when you know the key. Can you solve this? We've given you the encrypted flag, key, and a table to help UFJKXQZQUNB with the key of SOLVECRYPTO. Can you use this table to solve it?. 

## Solution

Looks like a Vigenere Cipher. Using the table and key for now and doing the manual way.

`picoCTF{CRYPTOISFUN}`

Less manual way would be in python3:

```
#!/usr/bin/env python3
  
import sys

ciphertext = sys.argv[1]
key = sys.argv[2]

key_length = len(key)
key_as_int = [ord(i) for i in key]
ciphertext_int = [ord(i) for i in ciphertext]
plaintext = ''
for i in range(len(ciphertext_int)):
    value = (ciphertext_int[i] - key_as_int[i % key_length]) % 26
    plaintext += chr(value + 65)
print(plaintext)
```

First argument would be your ciphertext, second would be the key.