#SWIFT Web Access
With full administrative control across the forest, the next mission was to access and abuse the internal **SWIFT payment system** hosted within the **BANK domain**, simulating a high-impact financial compromise.

## **Step 1: Accessing the JMP Box (Jump Host)**

From the **BANKDC**, using the **Enterprise Admin** account created earlier, I initiated a Remote Desktop Protocol (RDP) session to the **JMP box**.This jump host provided internal browser access to critical systems, most notably, the **SWIFT banking portal**

- [x]  **First Task - SWIFT Web Access**

- [x]  

Upon logging into the **E-CITIZEN portal**, I selected the task titled **“SWIFT Web Access”**, which laid out a simulated procedure mimicking a real-world SWIFT transaction flow.

### **Transfer Information:**

      **SWIFT Transfer Workflow (as provided):**

            1. A customer requests a funds transfer and is assigned a **Transfer                Code**.

     2. The customer shares this code with the bank.

3. A **Capturer** authenticates into the SWIFT application and logs the transaction.

4. An **Approver** then reviews and approves the transaction using the **JMP host**.

5. Upon approval, the transaction is sent through the SWIFT network and the customer is notified.

## **Step 2: Executing the Task – Simulating a Fraudulent SWIFT Transfer**

### Following the provided procedure:

      1. I launched **Google Chrome** from the JMP host.

2. Navigated to the SWIFT Banking Portal at https://swift.bank.thereserve.loc

3. Logged in using a **dummy user account**.

4. Clicked **“Make a Transaction”**.

5. Entered the transaction details:

o **Sender ID:** Source Account ID (dummy)

o **Receiver ID:** Destination Account IDo **Amount:** $10,000,000

6. Upon submission, the portal requested a confirmation PIN code, simulating an email-based second factor.

o However, as per **E-CITIZEN instructions**, no actual email check was needed.

7. I returned to the **E-CITIZEN portal** and confirmed the transaction by entering Y.

![image.png](attachment:1ccb81ee-c43a-4262-ae97-a379a6f3ca3e:image.png)

![image.png](attachment:1baa313d-e84e-42e6-95a1-b71f10300d72:image.png)

![image.png](attachment:0ee5faf8-e120-4b15-8ac9-70651a654187:image.png)

![image.png](attachment:25fce6ed-6dd0-44fb-870c-ac6ebe56838f:image.png)

### Flag-17: Access to SWIFT application: THM{6bc2f0f0-1eda-47bd-9eb2-8abff4a5d4d1}
