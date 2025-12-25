**Users and Groups Administration in Linux**

# Users and Groups

• User → A person (or process) that uses the operating system services.\
• Group → A collection of users. Groups are used to manage permissions
more easily.

# Types of Users in Linux

1.  Super user / Root (UID = 0)\
    - Has all permissions and privileges.\
    - Can manage users, groups, services, hardware, and files.\
    \
    2. Static System Users (UID 1--200)\
    - Created automatically by the OS.\
    - Examples: daemon, bin, sys.\
    \
    3. System Users (UID 201--999)\
    - Created when packages or services are installed.\
    - Example: apache (for web server), named (DNS), chronyd (time
    sync).\
    \
    4. Normal Users (UID 1000--60000)\
    - Created manually by the system administrator.\
    - Have limited permissions.

    **Important User & Group Files**

<!-- -->

1.  Cat /etc/passwd :

    ![](images/media/image1.png){width="5.756944444444445in"
    height="3.58125in"}

<!-- -->

2.  cat /etc/shadow:

    ![](images/media/image2.png){width="5.491666666666666in"
    height="7.233333333333333in"}

3.  cat /etc/group:

    ![](images/media/image3.png){width="5.508333333333334in"
    height="7.708333333333333in"}

4.  cat /etc/gshadow:

    ![](images/media/image4.png){width="5.266666666666667in"
    height="7.366666666666666in"}

<!-- -->

2.  **Cat /etc/passwd**

Format:\
username : password_mask : UID : GID : comment : home_directory :
login_shell\
\
• username → Login name of the user.

![](images/media/image5.png){width="5.7625in" height="0.71875in"}

• password_mask (x) → Password is not stored here, only a placeholder
(x). Actual password is in /etc/shadow.

![](images/media/image6.png){width="5.761111111111111in"
height="0.41180555555555554in"}

• UID → Unique User ID (0 = root, 1000+ = normal users).

![](images/media/image7.png){width="5.7625in" height="0.35in"}

• GID → Primary Group ID (refers to /etc/group).

![](images/media/image8.png){width="5.767361111111111in"
height="0.6881944444444444in"}

• comment → Description about the user (full name, etc.).

![](images/media/image9.png){width="5.7659722222222225in"
height="0.6048611111111111in"}

• home_directory → Default directory after login (usually
/home/username).

![](images/media/image10.png){width="5.761111111111111in"
height="0.6583333333333333in"}

• login_shell → Default shell (/bin/bash, /bin/sh, etc.).

![](images/media/image11.png){width="5.7659722222222225in"
height="0.4895833333333333in"}

3.  cat /etc/shadow

• username → Same as in /etc/passwd.

![](images/media/image12.png){width="5.768055555555556in"
height="0.3611111111111111in"}

• encrypted_password → Encrypted (hashed) password. ! or \* means
account is locked.

![](images/media/image13.png){width="5.761111111111111in"
height="0.4861111111111111in"}

• last_change → Days since 1 Jan 1970 when password was last changed.

![](images/media/image14.png){width="5.761805555555555in"
height="0.3888888888888889in"}

• min → Minimum days before password can be changed.

![](images/media/image15.png){width="5.767361111111111in"
height="0.3701388888888889in"}

• max → Maximum days before password must be changed.

![](images/media/image16.png){width="5.761111111111111in"
height="0.37777777777777777in"}

• warn → Number of days before expiry when user is warned.

![](images/media/image17.png){width="5.767361111111111in"
height="0.42083333333333334in"}

• inactive → Days after expiry before account is disabled.

![](images/media/image18.png){width="5.763888888888889in"
height="0.41041666666666665in"}

• expire → Absolute account expiry date (days since 1970).

![](images/media/image19.png){width="5.761805555555555in"
height="0.36180555555555555in"}

• reserved → Future use (kept empty).\
![](images/media/image20.png){width="5.756944444444445in"
height="0.38055555555555554in"}

**4\] cat /etc/group**

• groupname → Name of the group.

![](images/media/image21.png){width="3.0416666666666665in"
height="1.1083333333333334in"}

• password → Rarely used, usually x. Group passwords are in
/etc/gshadow.

![](images/media/image22.png){width="2.8916666666666666in"
height="1.1in"}

• GID → Group ID (matches with users' GID).

![](images/media/image23.png){width="2.591666666666667in"
height="0.9083333333333333in"}

• members → Comma-separated list of users in this group.

![](images/media/image24.png){width="2.3916666666666666in"
height="1.0in"}

**5\] cat /etc/gshadow**

• groupname → Group name.

![](images/media/image25.png){width="3.158333333333333in"
height="1.1083333333333334in"}

• group_password → Encrypted group password (rarely used).

![](images/media/image26.png){width="3.075in"
height="0.7666666666666667in"}

• admins → Users who can manage the group.

![](images/media/image27.png){width="2.7416666666666667in"
height="1.225in"}

• members → Regular group members.

![](images/media/image28.png){width="2.7916666666666665in"
height="1.5666666666666667in"}

**User Management Commands**

> • Create user: useradd username\
> • View users: cat /etc/passwd

![](images/media/image29.png){width="5.767361111111111in"
height="3.4923611111111112in"}

• Check user ID & group info:\
id username

![](images/media/image30.png){width="5.7652777777777775in"
height="0.8069444444444445in"}

id -un username \# shows username

id -gn username \# shows primary group

id -Gn username #shows primary and secondary

id -u username #shows user id

id -g username #shows group id

![](images/media/image31.png){width="5.768055555555556in"
height="4.754166666666666in"}

• Set password: passwd username

![](images/media/image32.png){width="5.761805555555555in"
height="1.4597222222222221in"}

• Remove password: passwd -d username

![](images/media/image33.png){width="5.558333333333334in"
height="1.525in"}

• Delete user: userdel username

• Delete user with home/mail: userdel -r username

# 
