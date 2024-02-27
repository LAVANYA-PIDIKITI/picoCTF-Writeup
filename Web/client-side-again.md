# Client Side Again
AUTHOR : DANNY <br>
DESCRIPTION : Can you break into this super secure portal? <br>
https://jupiter.challenges.picoctf.org/problem/6353/ (link) or http://jupiter.challenges.picoctf.org:6353

# Solution

Open the inspect tab and go the Sources tab where the HTML of the page can be viewed. <br>
Inside the Script tags, you will find <br>
`var _0x5a46=['0a029}','_again_5','this','Password\x20Verified','Incorrect\x20password','getElementById','value','substring','picoCTF{','not_this'];`

Concatenate the flag and submit it to get points
