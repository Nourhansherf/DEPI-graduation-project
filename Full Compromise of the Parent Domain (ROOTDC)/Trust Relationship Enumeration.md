# Trust Relationship Enumeration 
### With full control over CORPDC, the next logical target was the root domain controller: 
### ROOTDC.thereserve.loc (10.200.40.21) 


Using PowerShell from CORPDC, I verified the bidirectional trust relationship with the
root domain:

> ```text
>Import-Module ActiveDirectory 
> Get-ADTrust -Filter *
> ```
<img width="752" height="411" alt="Image1" src="https://github.com/user-attachments/assets/3aa20be3-ba28-4493-a4e9-71b4fd9df02d" />


The result we have confirmed a two-way trust between corp.thereserve.loc and thereserve.loc,enabling privilege escalation across domains.

### **Now we need to perform Golden Ticket Attack  so we need this:**
1.Domain SID

2.NTLM hash of the KRBTGT account

3.FQDN of the target domain

4.Username to impersonate (e.g., Administrator)

i already have  Domain Admin rights so I proceeded to disable Windows Defender to avoid detection:
> ```text
> Set-MpPreference -DisableRealtimeMonitoring $true
> ```
Then transferred mimikatz.exe from my attacker machine to CORPDC using Python
HTTP server and Chrome Or just copy and paste using the RDP Access, depending on availability.
# DCSync Attack with Mimikatz : 
Using mimikatz, I performed a DCSync attack to extract the NTLM hash of the KRBTGT account:
### 1- Lunching mimikatz.exe
<img width="537" height="328" alt="image 2" src="https://github.com/user-attachments/assets/b89c8775-2fb8-49bf-82ed-5aa218ff83a7" />

### 2- Extract the NTLM hash 
<img width="537" height="352" alt="image3" src="https://github.com/user-attachments/assets/e4373522-2e84-44be-ac7c-06d97ec21088" />

KRBTGT NTLM hash: 0c757a3445acb94a654554f3ac529ede 
### 3- Get SID of the CopDC & ROOT domain :
<img width="746" height="462" alt="image 4" src="https://github.com/user-attachments/assets/433fb72e-0092-4eb2-8ea1-0c509812ba49" />


