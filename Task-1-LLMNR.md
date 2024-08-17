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


 dd files via upload
# Task 2: Create a GPO—Account Lockout

**Objective:** Implement an account lockout policy on your Windows workstation.

## Instructions

1. **Create a New GPO:**
   - In **Group Policy Management**, right-click **Group Policy Objects** and select **New**.
   - Name the new GPO **Account Lockout** and click **OK**.

2. **Edit the GPO:**
   - Right-click the **Account Lockout** GPO and select **Edit**.
   - Navigate to **Computer Configuration** > **Policies** > **Windows Settings** > **Security Settings** > **Account Policies** > **Account Lockout Policy**.
   - Configure the settings:
     - **Account lockout duration**: 15 minutes
     - **Account lockout threshold**: 10 invalid logon attempts
     - **Reset account lockout counter after**: 15 minutes
   - Click **OK** to apply the settings.

3. **Link the GPO:**
   - Go back to **Group Policy Management**.
   - Right-click on the **GC Computers** OU and select **Link an Existing GPO**.
   - Select the **Account Lockout** GPO and click **OK**.

![Account-Lockout-Policies](https://github.com/user-attachments/assets/c96cac50-10ec-4061-9ef7-3e50b3113f0a)



# Task 3: Create a GPO—Enabling Verbose PowerShell Logging and Transcription

**Objective:** Enable PowerShell logging and transcription through a GPO.

## Instructions

1. **Create a New GPO:**
   - In **Group Policy Management**, right-click **Group Policy Objects** and select **New**.
   - Name the new GPO **PowerShell Logging** and click **OK**.

2. **Edit the GPO:**
   - Right-click the **PowerShell Logging** GPO and select **Edit**.
   - Navigate to **Computer Configuration** > **Policies** > **Administrative Templates** > **Windows Components** > **Windows PowerShell**.
   
   - **Enable Module Logging:**
     - Double-click **Turn on Module Logging**.
     - Set it to **Enabled**.
     - Click **Show** next to **Module Names** and enter `*` (wildcard).
     - Click **OK**.

   - **Enable Script Block Logging:**
     - Double-click **Turn on PowerShell Script Block Logging**.
     - Set it to **Enabled**.
     - Check **Log script block invocation start/stop events**.
     - Click **OK**.

   - **Enable Script Execution:**
     - Double-click **Turn on PowerShell Script Execution**.
     - Set it to **Enabled**.
     - Choose **Allow all scripts**.
     - Click **OK**.

   - **Enable Transcription:**
     - Double-click **Turn on PowerShell Transcription**.
     - Set it to **Enabled**.
     - Leave the Transcript output directory blank.
     - Check **Include invocation headers**.
     - Click **OK**.

3. **Link the GPO:**
   - Go back to **Group Policy Management**.
   - Right-click on the **GC Computers** OU and select **Link an Existing GPO**.
   - Select the **PowerShell Logging** GPO and click **OK**.
  
   ![Windows-PowerShell-Policies](https://github.com/user-attachments/assets/df1c94f4-a9b1-4fb1-acd8-07c53e7bd6a5)

# Task 4: Create a Script—Enumerate Access Control Lists

**Objective:** Create a PowerShell script to enumerate ACLs of files and directories.

## Instructions

1. **Create the PowerShell Script:**
   - Open a text editor and paste the following script:

     ```powershell
     $directory = Get-ChildItem -Path . -Directory
     foreach ($item in $directory) {
         $acl = Get-Acl -Path $item.FullName
         Write-Output "ACL for $($item.FullName):"
         $acl | Format-List
     }
     ```

   - Save the file as example: `enum_acls.ps1` in `C:\Users\sysadmin\Documents`.

2. **Test the Script:**
   - Open PowerShell and navigate to a directory (e.g., `cd C:\Windows`).
   - Run the script: `C:\Users\sysadmin\Documents\enum_acls.ps1`.
   - Verify that the ACL output for each file or subdirectory is displayed.
  
   
  
Congratulations and Thanks for Following Along!
Thank you for accessing and following the instructions in this repository! 🎉

You have successfully tackled a range of important security tasks:

Disabling Local Link Multicast Name Resolution (LLMNR): By implementing this policy, you've mitigated a significant vulnerability in your Windows environment.

Implementing an Account Lockout Policy: You've set up an account lockout policy to protect against brute-force attacks, enhancing the security of user accounts.

Enabling Verbose PowerShell Logging and Transcription: Your efforts to configure PowerShell logging will improve visibility and forensics capabilities on your system.

Creating a Script to Enumerate Access Control Lists (ACLs): You've developed a script to retrieve and review ACLs, crucial for managing permissions and security.

Your proactive approach to these tasks not only boosts your understanding of Windows security management but also contributes to a more secure environment. Your hard work and attention to detail are greatly appreciated!

Feel free to explore additional configurations or improvements and contribute to the project if you have suggestions. Happy securing 
