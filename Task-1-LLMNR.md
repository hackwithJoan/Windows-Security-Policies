# Task 1: Disable Local Link Multicast Name Resolution (LLMNR)

**Objective:** Disable LLMNR on your Windows 10 machine via the GC Computers OU.

## Instructions

1. **Open Group Policy Management:**
   - Open **Server Manager**.
   - Click on **Tools** and select **Group Policy Management**.

2. **Create a New GPO:**
   - Right-click **Group Policy Objects** and select **New**.
   - Name the new GPO **No LLMNR** and click **OK**.

3. **Edit the GPO:**
   - Right-click the **No LLMNR** GPO and select **Edit**.
   - Navigate to **Computer Configuration** > **Policies** > **Administrative Templates** > **Network** > **DNS Client**.
   - Find and double-click **Turn Off Multicast Name Resolution**.
   - Set it to **Enabled** and click **OK**.

4. **Link the GPO:**
   - Return to **Group Policy Management**.
   - Right-click on the **GC Computers** OU and select **Link an Existing GPO**.
   - Select the **No LLMNR** GPO and click **OK**.
  
 ![NO_LLMR](https://github.com/user-attachments/assets/a57801dd-5d24-4e2f-8ede-1db7dabf1b71)

