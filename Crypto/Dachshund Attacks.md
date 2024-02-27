# Dachshund Attacks
AUTHOR: SARA

Description
What if d is too small? Connect with `nc mercury.picoctf.net 36463`.

# Solution
Credits to the owner
```python
from pwn import *
import owiener

host = args.HOST or 'mercury.picoctf.net'
port = int(args.PORT or 36463)
io = connect(host, port)

io.recvline()
e = int(str(io.recvline(), "ascii").split(": ")[1].strip())
n = int(str(io.recvline(), "ascii").split(": ")[1].strip())
c = int(str(io.recvline(), "ascii").split(": ")[1].strip())
print("e = %i" % e)
print("n = %i" % n)
print("c = %i" % c)


d = owiener.attack(e, n)

# Below is based on https://rosettacode.org/wiki/RSA_code#Python
decrypted_text = pow(c, d, n)
print("Flag: %s" % binascii.unhexlify(hex(decrypted_text)[2:]).decode())
```
or
![image](https://github.com/LAVANYA-PIDIKITI/picoCTF-Writeup/assets/98797256/2522777d-4961-40e0-903d-a4b314180f53)
