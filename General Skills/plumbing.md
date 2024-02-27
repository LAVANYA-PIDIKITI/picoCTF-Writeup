# plumbing
AUTHOR: ALEX FULTON/DANNY TUNITIS

Description
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 7480`

# Solution:
Now connect using the command `nc jupiter.challenges.picoctf.org 7480`. Next you can see it prints some various strings , and as the hint says to use pipe try using 
`nc jupiter.challenges.picoctf.org 7480 | grep pico`.

![image](https://github.com/LAVANYA-PIDIKITI/picoCTF-Writeup/assets/98797256/39d7f695-bfc4-4597-a920-990c75f67149)
