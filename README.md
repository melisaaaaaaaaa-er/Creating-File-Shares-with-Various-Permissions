# Creating File Shares with Various Permissions

<h3>Purpose</h3>

- Creating and observing the effects of different file share permissions on Windows Server.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/17.png"/>

On Client-1, logon as a regular user. Choose one of the accounts generated with the script in a previous lab.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/18.png"/>

On DC-1, make sure you are logged in as an administrator (i.e. jane-admin).

Go to the C:\ drive and create the following folders:
- read-access
- write-access
- no-access
- accounting

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/19.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/20.png"/>

Right-click the folder → Properties → Sharing → Share... 

Add Domain Users and select the Read option from the drop-down menu on the right. Select “Share”.

Repeat these steps for the other folders as well:
- Write-access – Domain Users, Read/Write
- No-access – Domain Admins, Read/Write

Ignore the accounting folder for now.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/19.5.png"/>

In the read-access folder, create a sample text document.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/24.png"/>

On Client-1, open the File Explorer and navigate to \\dc-1 through the search bar at top. The share folders created on DC-1 will show up. Try to access each of them and see what happens.

For the no-access folder, you will be denied access as the user account you are logged in to is not a member of the Domain Admins group. It is just a regular user account (Domain Users). 

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/25.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/26.png"/>

For the read-access folder, you should be able to access it and the contents within, but you will not be permitted to create new files or make changed to existing ones.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/27.png"/>

For the write-access folder, you should be able to access the folder itself as well as any contents within it. You will also be able to add your own files to it and make changes to existing ones.

#
<h3>The accounting folder</h3>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/28.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/29.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/30.png"/>

On DC-1, go to ADUC and create a new security group called Accountants in an OU named _SECURITY_GROUPS.

Right-click _SECURITY_GROUPS → New → Group 

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/31.png"/>

Go back to the accountants folder in File Explorer and give the Accountants group Read/Write share permissions.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/32.png"/>

On Client-1, try to access the accountants folder. You will be denied as the user account is not a part of the Accountants security group.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/33.png"/>

On DC-1, assign the user account logged in to Client-1 to the Accountants group.

You will need to log off and log back on to Client-1 with the same account as share permissions are imposed during log on. They won’t apply to an account that is already logged on.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/34.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/network-file-shares-and-permissions-images/main/35.png"/>

Once you have logged on again to Client-1, you will be able to access and make changed to the accounting folder.
