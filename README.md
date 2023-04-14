# Beaufort Cipher
The Beaufort cipher is a type of polyalphabetic substitution cipher. It is similar in structure to
the Vigenère cipher, but uses a slightly modified enciphering mechanism.

## What is the Beaufort Cipher?
The Playfair cipher is a cryptographic technique that was invented in the 19th century by Sir 
Francis Beaufort. Its most famous application was in a rotor-based cipher machine, the Hagelin 
M-209. In the Beaufort cipher, each letter of the plaintext is encrypted using a different 
shift cipher based on a keyword.

## How does the Beaufort Cipher work?
Similar to the Vigenère cipher, the Key is a string of arbitrary length, and it gets repeated
enough times to create a new string with the same length as the plaintext. This string must be 
able to cover the entirety of the plaintext, so the it may be slightly longer then the given plaintext.

For the Encryption process, a letter from the plaintext and its corresponding key letter (based 
on the string created earlier) are chosen. If the alphabet is numbered from 0 to 25 (with A being 
0 and Z being 25), the ciphertext is generated by finding the difference between the key letter 
and the chosen plaintext letter key letter (mod 26).

As an example, if the key is `CIPHER` and the plaintext is `beaufort`, the following operation 
occurs:
```
C I P H E R C I    ->     2   8   15  7   4   17  2   8 
b e a u f o r t    ->   - 1   4   0   20  5   14  17  19
                        __________________________________ (mod 26)
                          1   4   15  13  25  3   11  15
                          B   E   P   N   Z   D   L   P
```

<img src="Beaufort Table Guide.jpg" height=600 width=600 align="center">
The ciphertext can be generated using the table above as well. If the example

The decryption process is the exact same as the encryption process. The key is used to 
generate a new string with the same length as the ciphertext, and the same process of finding 
the difference between the key and the chosen letter is applied here.

## Usage
```python
from beaufort_cipher import BeaufortCipher

# Instantiate a Beaufort Cipher object with a key
cipher = BeaufortCipher("LEMON")

# Encrypt a message
encrypted_text = cipher.encrypt("hello World")
print(encrypted_text)

# Decrypt a message
decrypted_text = cipher.decrypt(encrypted_text)
print(decrypted_text)
```

The result will be:
```
EABDZPQVDK
helloworld
```

## References
- <a href="https://en.wikipedia.org/wiki/Beaufort_cipher"> Wikipedia: Beaufort Cipher</a>
