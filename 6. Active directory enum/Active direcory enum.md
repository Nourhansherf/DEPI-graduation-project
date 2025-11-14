# Active directory enumeration (6)

Author: Nourhan Sherif
Status: Published
Category: PRD
Last edited time: October 25, 2025 3:06 PM
Created time: October 9, 2025 3:30 PM

using this credintials :

`mohammad.ahmed@corp.thereserve.loc:Password1!`

`laura.wood@corp.thereserve.loc : Password1@`

i used `remmina` to try to connect to this users PC’s

![image.png](image.png)

and we get into this machine 

![image.png](image%201.png)

so to submit the first flag i should search for that

![image.png](image%202.png)

so i will open the command prompt and see the host

![image.png](image%203.png)

![image.png](image%204.png)

![image.png](image%205.png)

and we got the first flag !

![image.png](image%206.png)

`THM{18800db2-ef64-4544-9bb7-56ba2dfa31ea}`

doing the same for the next flag

![image.png](image%207.png)

`THM{febcc4c0-b939-11ed-afa1-0242ac120002}`

doing the same we got the third one 

![image.png](image%208.png)

`THM{0ad79d03-5078-4970-ab91-ab24de6892a4}`

tried to see the other user 

![image.png](image%209.png)

seeing what we can find from the VPN Portal Login

![image.png](image%2010.png)

![image.png](image%2011.png)

now we have access to this user vpn

and i tried the other users email because it looks like it does not check the user creds to allow him access the vpn and it work 
we can connect to any users vpn
and i checks if it is checking that this user is in the company or not and it does not i can make my own vpn!!!

![image.png](image%2012.png)

![image.png](image%2013.png)

i tried to know which is in the admin group 

and i got this 

![image.png](image%2014.png)

so using the VPN findings ……

we can upload a reverse shell because it is not checking any thing it just take a file name 

so i used pentest monkey reverse shell to do this 

![image.png](image%2015.png)

i put my own ip 

![image.png](image%2016.png)

i opened a listener 

![image.png](image%2017.png)

just put it here

![image.png](image%2018.png)

and we got a shell

![image.png](image%2019.png)

![image.png](image%2020.png)

so we can cp any files !!

okay i have generated a rsa public key

![image.png](image%2021.png)

```html
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDaTSKkoC9yNAF8CeSEjoB4QMZl75x19Phxwhc0AElAVl87DnuTENhEt6Nfnj4WvYdL6jWFR0wtCbSoGr2vskKCajEpRsOMehNpO/MeNFjbRtw+sQtJHMyBgh9hVmMLkZ5LWDBNJU6KIMZPw/v54zmYvM94oGiuMK3feX4kVvGLtbBPOT5N/MYU44Hh3idS+6J9hMxarsxqPAkT6QRYFQfu62wQkhNmVbOi+QV1O8OJi6Qli7RXobp3pqN3cQGYPl3bHpOlgRfbvVud9fjGYw2oN6C9cdkeB5+JufFtbjM0HwY+tdqlDoR/KcqdQoN1Kq8RgDTbFtJc0KhR8eA0ZrKOeTtKF7W7TvU5mo8tc09fwLaQZmh22BCw740FQQZr3kCa/wi53FlXS0hnnVSBy/97Wz+eznWlZ0mtpdCWTg09WDPXOGxZcl9IDapjjw8DB4hKVd57IhxIPtvVJD8IOQK6aEXf10tjA4jf0GAELD7fjTU6gS/c219a/T4NnxU3SzE= nourhan@kali
```

then i go to gtfobins.github to see what i can do with the cp command

![image.png](image%2022.png)

and i can read the authorized keys 

![image.png](image%2023.png)

and we got connected to the ssh

![image.png](image%2024.png)

![image.png](image%2025.png)

![image.png](image%2026.png)

and i downloaded the reverse shell 

![image.png](image%2027.png)

and we get a meterpreter shell 

![image.png](image%2028.png)

![image.png](image%2029.png)

![image.png](image%2030.png)

`THM{2540046c-b93b-11ed-afa1-0242ac120002}`

![image.png](image%2031.png)