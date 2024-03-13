# Creating File Shares with Various Permissions

![17](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/6a25f394-0f6c-47ea-bbbc-e6fc8fda8a8b)

On Client-1, logon as a regular user. Choose one of the accounts generated with the script in a previous lab.

#
![18](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/07df53fa-4bc0-4a1e-8e40-0c92072dfb6b)

On DC-1, make sure you are logged in as an administrator (i.e. jane-admin).

Go to the C:\ drive and create the following folders:
- read-access
- write-access
- no-access
- accounting

#
![19](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/e04203ad-debf-4795-8b0f-59f3d4aa8492)

![20](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/d536f762-f672-4c35-9450-22a6b5d3db38)

Right-click the folder → Properties → Sharing → Share... 

Add Domain Users and select the Read option from the drop-down menu on the right. Select “Share”.

Repeat these steps for the other folders as well:
- Write-access – Domain Users, Read/Write
- No-access – Domain Admins, Read/Write

Ignore the accounting folder for now.

#
![19 5](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/394f6ffc-2f55-4b66-918c-f5e010764faf)

In the read-access folder, create a sample text document.

#
![24](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/182444ca-5b2b-4188-ba63-5fa0650aa715)

On Client-1, open the File Explorer and navigate to \\dc-1 through the search bar at top. The share folders created on DC-1 will show up. Try to access each of them and see what happens.

For the no-access folder, you will be denied access as the user account you are logged in to is not a member of the Domain Admins group. It is just a regular user account (Domain Users). 

#
![25](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/a4d8e2b8-467d-4ece-840d-b225f9fc18c2)

![26](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/3ecea965-3848-4f46-ab57-a1ace2544b63)

For the read-access folder, you should be able to access it and the contents within, but you will not be permitted to create new files or make changed to existing ones.

#
![27](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/05d8d355-e243-48da-94ad-3499d63e8819)

For the write-access folder, you should be able to access the folder itself as well as any contents within it. You will also be able to add your own files to it and make changes to existing ones.

#
<h3>The accounting folder</h3>

![28](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/72583385-6163-4b7b-bf42-ddfb08b2b7f7)

![29](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/78074e28-4cef-43ad-9809-5b1100accae0)

![30](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/f7fcacd5-8395-4201-8678-7667880998ed)

On DC-1, go to ADUC and create a new security group called Accountants in an OU named _SECURITY_GROUPS.

Right-click _SECURITY_GROUPS → New → Group 

#
![31](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/1b802721-cf30-4c60-9fba-91ffb86d3079)

Go back to the accountants folder in File Explorer and give the Accountants group Read/Write share permissions.

#
![32](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/081679b5-83ab-483f-98e0-6879cb227fa6)

On Client-1, try to access the accountants folder. You will be denied as the user account is not a part of the Accountants security group.

#
![33](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/82729112-4db5-48a2-b863-c8fd0fcdafdf)

On DC-1, assign the user account logged in to Client-1 to the Accountants group.

You will need to log off and log back on to Client-1 with the same account as share permissions are imposed during log on. They won’t apply to an account that is already logged on.

#
![34](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/0eccc7ed-8a05-428b-b6bc-353d95ac4fd8)

![35](https://github.com/melisa-er/Creating-File-Shares-with-Various-Permissions/assets/157723219/89b72abb-813e-44d0-b05e-d75a30973c1a)

Once you have logged on again to Client-1, you will be able to access and make changed to the accounting folder.
