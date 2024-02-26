# PW Crack 5
AUTHOR: LT 'SYREAL' JONES

Description
Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too. Here's a dictionary with all possible passwords based on the password conventions we've seen so far.

# Solution:
It's simple, you add one more line of opening the dictionary.txt and iterate through the same.<br>
Here's the modifed code
```python
import hashlib

### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_5_pw_check():
    with open('dictionary.txt', 'r') as dictionary_file:
        potential_passwords = [line.strip() for line in dictionary_file]

    for potential_pw in potential_passwords:
        potential_pw_hash = hash_pw(potential_pw)
        if potential_pw_hash == correct_pw_hash:
            print("Welcome back... your flag, user:")
            decryption = str_xor(flag_enc.decode(), potential_pw)
            print(decryption)
            return
    print("That password is incorrect")



level_5_pw_check()

```
![image](https://github.com/LAVANYA-PIDIKITI/picoCTF-Writeup/assets/98797256/113afc2e-b9f4-4e0c-993a-85d69cdb15bc)
