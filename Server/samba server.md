# SAMBA SERVER

Package: Samba

Port number: 139, 445 and 137, 138

Configuration File: /etc/samba/smb.conf

Services: smb.service

## Steps to Configure Samba Server

1\. Install the Samba package:\
\# yum install samba

![](media/image1.tmp){width="6.0in" height="3.4125in"}

2\. Modify the Samba configuration file:\
\# vi /etc/samba/smb.conf

![](media/image2.tmp){width="3.354339457567804in"
height="0.48613626421697287in"}

![](media/image3.tmp){width="3.3404494750656166in"
height="1.1389479440069992in"}

3\. Start and enable the Samba service:\
\# systemctl enable \--now samba

![](media/image4.tmp){width="6.0in" height="0.24791666666666667in"}

4\. Create a Samba user and set an SMB password:\
\# useradd sambauser

![](media/image5.tmp){width="2.6598589238845145in"
height="0.2569575678040245in"}

\# smbpasswd -a sambauser

![](media/image6.tmp){width="3.020988626421697in"
height="0.902823709536308in"}

5\. Install the Samba client package:\
\# yum install samba-client

![](media/image7.tmp){width="6.0in" height="3.025in"}

6\. Ensure that the directory has been shared or not:\
\# smbclient -L [\\\\localhost](file:///\\localhost)

![](media/image8.tmp){width="5.062760279965004in"
height="1.951489501312336in"}

7\. In Windows:\
- Press Win + R\
- Enter the shared folder path (e.g.,
\\\\\<server_ip\>\\\<share_name\>)\
- Enter the Samba username and password to access the files.

![A screenshot of a computer AI-generated content may be
incorrect.](media/image9.tmp){width="4.858333333333333in"
height="4.25in"}

![](media/image10.tmp){width="6.0in" height="2.7618055555555556in"}
