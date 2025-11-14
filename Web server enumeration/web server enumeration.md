# Web server enumeration (2)

Author: Nourhan Sherif
Status: Published
Category: PRD
Last edited time: October 16, 2025 11:41 AM
Created time: October 8, 2025 6:00 PM

[http://swift.bank.thereserve.loc/](http://swift.bank.thereserve.loc/)

### To do list:

- Browse the website:
    - check for usernames, emails, anything that might be used for attacks [especially phishing]
- check the source code
- check robots.txt
- `gobuster -dir search`
- `gobuster -vhosts`
- `nikto`

---

## The website :

when i was checking the website i figure out that 

![image.png](images/image.png)

when i open “Meet the Team” section every picture of a team member contains his full name

![image.png](images/image%201.png)

so what about seeing if there is directory listing for the images directory !!

![image.png](images/image%202.png)

so we got all the usernames of the bank system and i think it will be easy for getting their emails :)

so we got a possible attack path:

- possible phishing on this email with a word doc with malicious disguised as a resume?
- 

![image.png](images/image%203.png)

---

### Listing in /october/themes/demo/REAMME.md

found that there is something called October CMS

- computer management system
