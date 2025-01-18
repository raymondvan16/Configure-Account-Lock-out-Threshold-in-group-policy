<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Configure account Lockout threshold in group policy. (Active Directory)</h1>
defining settings that control when an account is locked after multiple failed login attempts, how long the account remains locked, and how the lockout counter is reset.


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Group Policy Management Console (GPMC)

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Open the Group Policy Management Console (GPMC)
- Step 2: Create or edit a Group Policy Object (GPO)
- Step 3: Navigate to the Account Lookout Policy Settings
- Step 4: Configure Account Lockout Policy Settings
- Step 5: Link the GPO to an Organizational Unit (OU)
- step 6: Update Group Policy
- Step 7: Verify the Policy

<h2>Step 1: Open the Group Policy Management Console (GPMC).</h2>
Log in to a machine with Group Policy Management Console installed (typically, a Domain Controller).
Click Start, and type gpmc.msc in the search box, then press Enter. This opens the Group Policy Management Console.
  
<h2>Step 2: Create or edit a Group Policy Object (GPO).</h2>
In the GPMC, navigate to the Group Policy Objects section.
Right-click Group Policy Objects and select New to create a new GPO, or right-click an existing GPO and select Edit to modify it.
Give the new GPO a descriptive name if you're creating a new one, like "Account Lockout Policy".

<h2>Step 3: Navigate to the Account Lookout Policy Settings</h2>
In the Group Policy Management Editor, expand the following:
Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy.

<h2>Step 4: Configure Account Lockout Policy Settings</h2>
You will see three primary settings that you need to configure:


  1.Account Lockout Duration:
    -Definition: The time in minutes that an account remains locked before it is automatically unlocked.
    -Configuration: Double-click on this setting, select Define this policy setting, and then set the duration (e.g., 30 minutes).
    
  2.Account Lockout Threshold:
    -Definition: The number of failed logon attempts that will trigger an account lockout.
    -Configuration: Double-click on this setting, select Define this policy setting, and then set the threshold (e.g., 3 invalid attempts).
    
  3.Reset Account Lockout Counter After:
    -Definition: The time in minutes after which the failed logon attempts counter is reset to 0, assuming there are no additional failed logon attempts.
    -Configuration: Double-click on this setting, select Define this policy setting, and then set the time (e.g., 15 minutes).


<h2>Step 5: Link the GPO to an Organizational Unit (OU)</h2>
-Once the GPO is configured, you need to link it to the appropriate Organizational Unit (OU) or domain where you want the policy to apply.

-In the GPMC, right-click the OU or domain where you want to apply the GPO and select Link an Existing GPO.
-Choose the GPO you created or modified earlier and click OK.


<h2>step 6: Update Group Policy</h2>
You can wait for the Group Policy to propagate automatically, or you can force an update immediately.
On a client machine or server, open Command Prompt and type gpupdate /force, then press Enter.

<h2>Step 7: Verify the Policy</h2>
To verify the policy, you can use the rsop.msc (Resultant Set of Policy) tool on a client machine to see the applied settings.
Alternatively, you can also check the settings using the Group Policy Management Console.

<br>End of Lab.</br>
