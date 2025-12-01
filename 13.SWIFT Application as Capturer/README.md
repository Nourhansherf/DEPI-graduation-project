## **SWIFT Application as Capturer**

Leverage domain access to impersonate a **SWIFT Capturer** and push a financial transaction through the internal **SWIFT application**.

![image.png](attachment:e17fcd93-f4b2-4456-89f5-aa6c681a72f0:image.png)

### **Initial Enumeration – Capturer Role Users**

With full access to **Active Directory Users and Computers**, I began by identifying users

who are members of the following SWIFT-specific roles:

- **Payment Capturers**
- **Payment Approvers**

These groups were located under the **Bank Domain Organizational Units (OUs)**.

Upon enumeration, I identified **multiple users** who held the **“Payment Capturer”** role.

One of them was:

• **User:** g.watson

![image.png](attachment:ff422aad-c495-4c4b-86fc-bda7a0fb3d35:image.png)

### **Step 1: Logging into WORK1 as Capturer**

Using my administrative access:

1. I initiated an **RDP session** to WORK1.

2. Once logged in, I began reviewing the user's desktop and file directories.

### **Step 2: Discovering SWIFT Credentials**

While exploring the Documents folder under g.watson, I discovered a file named **swift**.

- Upon opening the file, it revealed a **password string**.
- This was likely stored for convenient access to the **SWIFT banking portal**.

![image.png](attachment:03676abb-a924-4324-bc3c-391d53d62cd8:image.png)

### **Step 3: Logging into SWIFT as Capturer**

With the discovered credentials:

1. I navigated to http://swift.bank.thereserve.loc via browser.

2. Logged in as **user g.watson** using the extracted password.

3. Gained access to the **Capturer dashboard** within the SWIFT application.

![image.png](attachment:c4a9b2f1-cbce-4cfa-a0ee-dac88763a9dc:image.png)

![image.png](attachment:88105ab2-ac27-43c3-85fd-bbf8a174e51d:image.png)

### **Step 4: Forwarding the Transaction**

Inside the portal:

- I located the **pending transaction** awaiting Capturer approval.
- Clicked on **“Forward”** to push the transaction to the **Approver queue**.

This completed the role-based duty of the **Capturer** in the SWIFT transfer chain.

![image.png](attachment:beabf6c8-1efa-4b88-8faf-ae2424ed1558:image.png)

![image.png](attachment:d589dab1-d544-4d43-a665-ab2d68228842:image.png)

![image.png](attachment:bd83bcce-2661-450a-8588-03a271678340:image.png)

### Flag-18: Access to SWIFT application as capturer: THM{204768b4-0d1d-4e0d-82b5-6015ec81f548}
