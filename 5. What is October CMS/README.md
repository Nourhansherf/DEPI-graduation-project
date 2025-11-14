# October CMS (5)

Author: Nourhan Sherif
Status: Published
Category: PRD
Last edited time: October 18, 2025 5:12 PM
Created time: October 9, 2025 10:42 AM

because i don’t know what is October CMS so i asked chatgpt about it and i found that

![image.png](image.png)

so i tried to brute force how can i access this admin login

and after some time i got that

![image.png](image%201.png)

i tried admin/admin and intercept the request in burp and i found that

![image.png](image%202.png)

so i can make username enumeration

and this was given to us in the lab files:

![image.png](image%203.png)

so i have to make a custome list to specify the password policy so i will john the repper

and i make this custome list

![image.png](image%204.png)

and we got our list

![image.png](image%205.png)

and i stored it in a file 

![image.png](image%206.png)

using the names we got from the directly listing we found the i

![image.png](image%207.png)

i asked chatgpt to make me a script to add the email at the end of each name

![image.png](image%208.png)

![image.png](image%209.png)

and now i brute force using hydra and got this 

![image.png](image%2010.png)

`laura.wood@corp.thereserve.loc : Password1@`

and we got another one !!

![image.png](image%2011.png)

`mohammad.ahmed@corp.thereserve.loc:Password1!`
