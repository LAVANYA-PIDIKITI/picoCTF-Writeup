# basic-mod1
AUTHOR: WILL HONG

Description
We found this weird message being passed around on the servers, we think we have a working decryption scheme.
Download the message here.
Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})
# Solution:
It's simple to do where you take mod of each number and then map it to the corresponding to character.

Find the code below
```python
mapping = {
    0: 'A', 1: 'B', 2: 'C', 3: 'D', 4: 'E', 5: 'F', 6: 'G', 7: 'H', 8: 'I', 9: 'J',
    10: 'K', 11: 'L', 12: 'M', 13: 'N', 14: 'O', 15: 'P', 16: 'Q', 17: 'R', 18: 'S', 19: 'T',
    20: 'U', 21: 'V', 22: 'W', 23: 'X', 24: 'Y', 25: 'Z', 26: '0', 27: '1', 28: '2', 29: '3',
    30: '4', 31: '5', 32: '6', 33: '7', 34: '8', 35: '9', 36: '_'
}

def decode(number):
    r = number % 37
    return mapping[r]

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
![image](https://github.com/LAVANYA-PIDIKITI/picoCTF-Writeup/assets/98797256/959d58f0-86ac-46e8-952e-030c48312156)
