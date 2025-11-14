# VPN server enumeration (3)

Author: Nourhan Sherif
Status: Published
Category: PRD
Last edited time: October 9, 2025 11:46 PM
Created time: October 8, 2025 10:35 PM

### nmap scan:

`nmap -p- 10.200.118.12 -v`

![image.png](image.png)

`nmap -p 22,80 -A 10.200.118.12 -v`

![image.png](image%201.png)

---

### For the HTTP server:

i ran a vhost scan 

`gobuster vhost -u [http://10.200.118.12](http://10.200.118.12/) -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt` 

and a nikto scan `nikto -h [http://10.200.118.12](http://10.200.118.12/)`

and a dir scan `gobuster dir -u [http://10.200.118.12](http://10.200.118.12/) -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt` 

![image.png](image%202.png)

we got a “/vpn” in the directory scanning 

![image.png](image%203.png)

opening it we found OpenVPN config file:

![image.png](image%204.png)

after some trubleshooting i figureout that i need to change this to connect to the internal domain

![image.png](image%205.png)

so i changed it to `10.200.118.12`

and we successfully connected to the internal domain

![image.png](image%206.png)

![image.png](image%207.png)

from the opev vpn we just made i can understand that 

- my ip address ⇒ `12.100.1.8`
    - this ip makes me able to connect to this two machines
        - `10.200.118.21`
        - `10.200.118.22`

so we can’t ping this two windows machines because of the firewall so i tried to nmap them

`nmap -p- 10.200.118.21 -Pn -v` & `nmap -p- 10.200.118.22 -Pn -v` 

![image.png](image%208.png)

![image.png](image%209.png)

so i start doing a more targeted scan 

`nmap -p22,139,3389,135,445 -A 10.200.118.21 -Pn -v`

`nmap -p139,135,3389,445,22 -A 10.200.118.22 -Pn -v`

[10.200.118.21](https://www.notion.so/10-200-118-21-2860b484a02880308c88cf1743dfbbcb?pvs=21)

[10.200.118.22](https://www.notion.so/10-200-118-22-2860b484a028806bb1d0cde21e1b5940?pvs=21)