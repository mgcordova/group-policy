<p align="center">
<img src="https://www.techtarget.com/rms/onlineimages/whatis-group_policy_object-f_mobile.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Group Policy and Managing Accounts</h1>
This tutorial outlines the implementation group policies and managing accounts within active directory.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Configuring Account Lockout Threshold in Group Policy
- Configure Account Lockout Policy Settings
- Update Group Policy
- Verify the Policy
- Enable and Disable Accounts in Active Directory

<h2>Configuring Account Lockout Threshold in Group Policy</h2>

<p>Log into dc-1 and launch Group Policy Management Console (GPMC). Click Start, and type gpmc.msc this opens the Group Policy Management Console.</p>

![image](https://github.com/user-attachments/assets/8eda8e50-76c6-44f8-a363-527a358aa0c4)

<p>In the GPMC, navigate to the Group Policy Objects section.

Right-click Group Policy Objects and select New to create a new GPO named "Account Lockout Policy".</p>

![image](https://github.com/user-attachments/assets/675d2222-6419-443c-9800-d153ed4a5e64)

<p>Right Click the Account Lockout Policy and click Edit.

In the Group Policy Management Editor, expand the following
Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy</p>

![image](https://github.com/user-attachments/assets/e3eeee96-b547-458b-9a5a-06836ba6fa2f)

![image](https://github.com/user-attachments/assets/56056c07-4555-476c-91ab-ece435ba1585)

<hr>

<h2>Configuring Account Lockout Policy Settings</h2>

<p>Doule click Account lockout duration, click define this policy setting, then set the duration to 30 minutes. Apply and save the settings</p>

![image](https://github.com/user-attachments/assets/998fde76-f295-48d7-8ddd-dc5fdd6161dd)

<p>It will autofill out suggestions for the rest of the settings basesd on your duration. Click ok and save your changes</p>

![image](https://github.com/user-attachments/assets/69126b69-6c4d-4d6e-a65a-b12fbee47536)

<p>In the GPMC, right-click the OU or domain where you want to apply the GPO and select Link an Existing GPO.

Choose the GPO you created or modified earlier and click OK.
</p>

![image](https://github.com/user-attachments/assets/743255d5-4d79-40d2-b838-a10d70e5a596)

![image](https://github.com/user-attachments/assets/833c8c3c-146a-42e0-bdec-96f266e53680)

<p>Then you want to add Domain Users to the Security Filtering </p>

![image](https://github.com/user-attachments/assets/055f6a61-889c-4c1c-adad-4d81f71c4f09)

![image](https://github.com/user-attachments/assets/010a677a-a154-4f18-bdab-153bfa935208)

<p>Enforce the group policy by right clicking and clicking enforce</p>

![image](https://github.com/user-attachments/assets/1e2f4336-0714-4f57-a271-a816c6b1c85e)

<hr>

<h2>Updating Group Policy</h2>

<p>You can wait for the Group Policy to propagate automatically, or you can force an update immediately.

On a client-1, open Command Prompt and type gpupdate /force, then press Enter.</p>

![image](https://github.com/user-attachments/assets/74c4d722-6a12-4605-8929-4f59426c04d7)

![image](https://github.com/user-attachments/assets/6501c23e-7ee6-4a88-9760-ee8288fdfa59)

<hr>

<h2>Verifying the Policy</h2>

<p>You can either run powershell as an admin then run gpresult /r to verify the changes

Alternatively, you can also check the settings using the Group Policy Management Console.</p>

![image](https://github.com/user-attachments/assets/5ddd73bf-bd1b-4c75-ab1f-7aaeea41b3b5)

![image](https://github.com/user-attachments/assets/7e139d1b-f8f2-4271-a14b-aeb386654a37)

<hr>

<h2>Enabling and Disabling Accounts</h2>

<p>Log onto dc-1 and open Active Directory Users and Computeres

Select mydomain.com, _employees and pick a random account to lock out of. Remember the username [baha.jet for this example] and the password for all these accounts by defualt is Password1</p>

![image](https://github.com/user-attachments/assets/a5a827fd-fcbb-4b61-aa57-87ceed6b3e16)

<p>To lock out of this account try to connect to client-1 with this username, but wrong person six times. You will then be greeted by a locked out prompt. </p>

![{81052AD0-08C3-4294-9CAF-C120E340E5C0}](https://github.com/user-attachments/assets/0f06058c-4eb7-4472-841b-819af73889ab)

![image](https://github.com/user-attachments/assets/da8bd35e-f2c7-44ef-8c07-ad3619ceb4a0)

<p>Right click the domain, click find and search for the user you locked out and select the account.</p>

![image](https://github.com/user-attachments/assets/c7e9d326-dfca-401f-ada9-11263305dfe5)

![image](https://github.com/user-attachments/assets/b6a15702-3461-4aca-9ef1-4b5ebbc096df)

<p>Select account and unlock the account. Make sure to apply your changes. </p>

![image](https://github.com/user-attachments/assets/28571f43-2d10-4f21-aa82-270281489580)

<hr>

<p>I hope this tutorial helped you gain a better understanding of group policy and managing accounts in an active directory. This can be done easily on both PC and Mac, with the only extra step on Mac being the download of the Remote Desktop App.

Now that we're finished, make sure to CLEAN UP YOUR AZURE ENVIRONMENT to avoid any unnecessary charges.

Remember to close your Remote Desktop connection, delete the Resource Group(s) you created at the start of the tutorial, and verify that the Resource Group has been successfully deleted.</p>
