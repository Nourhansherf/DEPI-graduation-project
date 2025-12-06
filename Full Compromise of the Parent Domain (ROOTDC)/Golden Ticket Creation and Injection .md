# Golden Ticket Creation and Injection 
Now armed with all the necessary artifacts, I launched mimikatz again and crafted a Golden Ticket:

<img width="833" height="413" alt="image 5" src="https://github.com/user-attachments/assets/613a84da-8fb3-4496-81c7-9d46e518f0db" />

This injected a forged TGT (Ticket Granting Ticket) into memory, impersonating
the Administrator on the ROOT domain.

### Display Kerberos ticket:
<img width="525" height="247" alt="image 6" src="https://github.com/user-attachments/assets/b7a5c2df-9a63-4712-926b-f3a8377bad92" />

# ROOTDC Compromise :
I tested access to the root domain resources and verified successful authentication and control

<img width="807" height="582" alt="image 7" src="https://github.com/user-attachments/assets/d0e70e8f-7b06-448d-9123-6c3bceece232" />

# Elevating ROOTDC Access with PsExec:
While the Golden Ticket attack provided stealthy and privileged access to the ROOTDC, leveraging PsExec allows us to interact more directly with the system 
— ideal for follow-up tasks like privilege abuse, exfiltration, and lateral tool execution.
## Step 1: Upload PsExec to CORPDC using Python Server on our attacking 
machine and Chrome Browser to dowanload it. 

## Step 2: Launch Remote CMD on ROOTDC 
Now with PsExec on CORPDC, we can run: 

<img width="496" height="208" alt="image 8" src="https://github.com/user-attachments/assets/bd37ad51-0da0-4622-b20f-6764847b4176" />

This spawns a remote interactive command prompt on ROOTDC, allowing full command execution as Administrator. 
# Enterprise Persistence via Domain-Level User Creation 
Maintain permanent administrative access to the ROOTDC.thereserve.loc by embedding a trusted user into the Enterprise Admins group — the highest privilege level across all trusted domains in the forest.
### Create a New Enterprise Admin User via PowerShell 

<img width="767" height="567" alt="image 9" src="https://github.com/user-attachments/assets/24da878d-5945-4aef-a888-1113a2f5dc88" />

This grants the custom user full access to every domain in the Active Directory forest using the Enterprise Admin User: admin1 and Password : Pass123. 

# Verification: RDP into ROOTDC

<img width="832" height="587" alt="image 10" src="https://github.com/user-attachments/assets/c150b32c-98f2-49ab-9bc8-5af6168ffe78" />

<img width="687" height="563" alt="image 11" src="https://github.com/user-attachments/assets/a7e05d06-38e5-4fb7-80c8-e47e6b55af51" />

# Enterprise Admin Persistence Established
Now I have: 

•     Full forest-wide persistence 

•     High-trust access across ROOTDC and CORPDC 

•      Ability to manage Group Policies, domain trusts, users, and security configurations 

•     Flags 15 and 16 successfully claimed and control maintained 

# o Flag15 (Foothold on Parent Domain) 

<img width="875" height="528" alt="image 12" src="https://github.com/user-attachments/assets/6d4b1671-8ba2-48ed-810e-f1bdf1b5ba47" />

<img width="761" height="685" alt="image 13" src="https://github.com/user-attachments/assets/d7f8de18-e63a-4eb0-a344-fc916b8e06d0" />

<img width="757" height="716" alt="image 14" src="https://github.com/user-attachments/assets/636b002a-68c3-4b8d-b22a-871aefc91d61" />

## 🚩 Flag 15: THM{ee8d8803-0551-4867-b665-e4cbf70d2652}
# Flag16 (Administrative access to Parent Domain) 

<img width="877" height="538" alt="image" src="https://github.com/user-attachments/assets/e584ff32-6032-4f24-b6f5-029a1a2e8b89" />

<img width="787" height="612" alt="image 16" src="https://github.com/user-attachments/assets/dbb58b00-6e5d-4170-a436-6becc8a32edb" />

<img width="637" height="632" alt="image 17" src="https://github.com/user-attachments/assets/9617a204-8fc0-4ebf-91b9-7a3154e6f58b" />

## 🚩 Flag 16: THM{354ef832-add1-42f5-aba7-677062939ada}
