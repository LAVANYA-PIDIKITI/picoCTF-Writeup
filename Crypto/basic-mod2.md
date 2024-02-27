# basic-mod2
AUTHOR: WILL HONG

Description
A new modular challenge!
Download the message here.
Take each number mod 41 and find the modular inverse for the result. Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})

# Solution:
It's similar to mod1 challenge but with a slight twist of finding out inverse which we're gonna write a function for the same.
```python
mapping = {
    1: 'A', 2: 'B', 3: 'C', 4: 'D', 5: 'E', 6: 'F', 7: 'G', 8: 'H', 9: 'I', 10: 'J',
    11: 'K', 12: 'L', 13: 'M', 14: 'N', 15: 'O', 16: 'P', 17: 'Q', 18: 'R', 19: 'S', 20: 'T',
    21: 'U', 22: 'V', 23: 'W', 24: 'X', 25: 'Y', 26: 'Z', 27: '0', 28: '1', 29: '2', 30: '3',
    31: '4', 32: '5', 33: '6', 34: '7', 35: '8', 36: '9', 37: '_'
}

def mod_inverse(a, m):
    # Calculate modular inverse using extended Euclidean algorithm
    g, x, y = extended_gcd(a, m)
    if g != 1:
        raise Exception('Modular inverse does not exist')
    else:
        return x % m

def extended_gcd(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        g, x, y = extended_gcd(b % a, a)
        return (g, y - (b // a) * x, x)

def decode(number):
    r = number % 41
    inv = mod_inverse(r, 41)
    return mapping[inv]

def main():
    f = open("message.txt", "r", encoding="UTF-8")
    lst = f.read().split()

    dec_lst = []

    for i in range(len(lst)):
        dec_lst.append(decode(int(lst[i])))

    decoded_text = ''.join(dec_lst)
    print(decoded_text)

if __name__ == '__main__':
    main()
```
![image](https://github.com/LAVANYA-PIDIKITI/picoCTF-Writeup/assets/98797256/a340e4ae-697b-4479-9bad-af235fc5622b)
