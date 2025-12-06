With Enterprise Admin rights over the entire forest, the final phase involves pivoting into the BANK domain and achieving administrative control over all its tiers. 
## Step 1: Accessing BANKDC via RDP 
From the ROOTDC, we connected to the BANKDC (Domain Controller for the bank.thereserve.loc child domain) via RDP, using the Enterprise Admin credentials created earlier.

## Step 2: Creating a Domain Admin in BANK Domain 
To secure persistent access to the BANK domain, we repeated our standard user creation + privilege escalation steps, executed from a PowerShell console:
> ```text
>#Set password for the new user
>$pwd = ConvertTo-SecureString "Pass123" -AsPlainText -Force
>
>#Create the new user in BANK domain
>New-ADUser -Name admin1 -AccountPassword $pwd -PasswordNeverExpires
>$true -Enabled $true -Server "bankdc.bank.thereserve.loc"
>
>#Retrieve user and group objects
>$User = Get-ADUser -Identity admin1 -Server "bankdc.bank.thereserve.loc"
>$Group = Get-ADGroup -Identity "Domain Admins" -Server
>"bankdc.bank.thereserve.loc"
>
>#Add the user to Domain Admins group
>Add-ADGroupMember -Identity $Group -Members $User -Server
>"bankdc.bank.thereserve.loc"
> ```

This gave us full Domain Admin access within the BANK child domain.
## Step 3: Access to JMP Box and Additional Servers
While attempting to connect to the JMP box directly from the attacker machine, theconnection was rejected due to the port being closed for external access.

To bypass this restriction:

I RDP'd into the JMP box from BANKDC, using our privileged domain account.From there, I submitted the corresponding TIER 1 Admin flags. Using a newly created user  I was able to successfully log in and submit all the flags related to the BANKDC systems.

# Flags Achieved via E-Citizen Portal 
With this domain-wide compromise, we were able to log into the E-Citizen platform and successfully claim the following Flag 
### Flag 13 (Foothold on Bank Division Tier 0 Infrastructure) 

<img width="622" height="426" alt="image 1" src="https://github.com/user-attachments/assets/a9f515c0-2f2d-4959-aa32-843a0b465255" />

<img width="755" height="630" alt="image 2" src="https://github.com/user-attachments/assets/9c24a070-7af6-4b54-b21e-f608d88c4d08" />

<img width="692" height="622" alt="images 3" src="https://github.com/user-attachments/assets/9dfb4ff8-1c2c-4d92-9629-3ac4c3f29065" />

## 🚩 Flag 13: THM{2d2b9799-b378-403a-9600-fab5b1ba7b05}

### Flag 14 : Administrative access to Bank Division Tier 0 Infrastructure 

<img width="786" height="467" alt="images 4" src="https://github.com/user-attachments/assets/fb1f364a-79d3-40b9-8bba-62eed1c5308e" />

<img width="810" height="600" alt="images 5" src="https://github.com/user-attachments/assets/01dee590-8056-492e-b3b0-17388b92dec8" />

<img width="858" height="627" alt="images 6" src="https://github.com/user-attachments/assets/90d99e18-7982-42cd-a417-73d40b3e4bb8" />

## 🚩 Flag 14:  THM{fbf52b9c-b61d-4a3c-85ab-31e466532ef7}

