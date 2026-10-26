# Lab-Exercise---3---Hill-Cipher

## Aim:
To implement the Vigenère Cipher algorithm using Python for encryption and decryption of a plaintext message using a given key.

## Procedure:
1.Define the function vigenere_encrypt(plaintext, key) to encrypt the plaintext using the Vigenère Cipher.

2.Convert the plaintext and key into uppercase letters.

3.For each alphabetic character, calculate the corresponding key value and plaintext value using ASCII values.

4.Encrypt each character using the formula \(C = (P + K) \bmod 26\), where P is the plaintext value and K is the key value.

5.Define the function vigenere_decrypt(ciphertext, key) to decrypt the encrypted message using the formula \(P = (C - K) \bmod 26\).

6.Get the plaintext and key as input from the user.

7.Check whether the key contains only alphabetic characters.

8.If the key is valid, display the encrypted text and decrypted text. Otherwise, display an error message.

## Program:
```
def vigenere_encrypt(plaintext, key):
    plaintext = plaintext.upper()
    key = key.upper()
    ciphertext = ""
    j = 0
    
    for char in plaintext:
        if char.isalpha():
            row = ord(key[j % len(key)]) - ord('A')
            col = ord(char) - ord('A')
            
            # Use the Vigenere table
            encrypted = chr((row + col) % 26 + ord('A'))
            ciphertext += encrypted
            j += 1
        else:
            ciphertext += char
            
    return ciphertext

def vigenere_decrypt(ciphertext, key):
    ciphertext = ciphertext.upper()
    key = key.upper()
    plaintext = ""
    j = 0
    
    for char in ciphertext:
        if char.isalpha():
            row = ord(key[j % len(key)]) - ord('A')
            col = ord(char) - ord('A')
            
            # Find plaintext using the Vigenere table
            decrypted = chr((col - row) % 26 + ord('A'))
            plaintext += decrypted
            j += 1
        else:
            plaintext += char
            
    return plaintext

message = input("Enter plaintext: ")
key = input("Enter key: ")

if key.isalpha():
    encrypted = vigenere_encrypt(message, key)
    print("Encrypted text:", encrypted)
    
    decrypted = vigenere_decrypt(encrypted, key)
    print("Decrypted text:", decrypted)
else:
    print("Key must contain only alphabets.")
```
## Output:

<img width="1593" height="830" alt="image" src="https://github.com/user-attachments/assets/39df984e-d441-4f0b-80b1-8bf79678cf3a" />


## Result:

Thus, the Vigenère Cipher algorithm was implemented successfully in Python for encryption and decryption using a valid key.
