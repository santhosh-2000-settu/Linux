# Types of File Permissions

Linux file permissions are critical for system security and proper file
sharing. There are three main types of file permissions:\
• Basic Permissions: Read, write, and execute.\
• Special Permissions: Setuid, setgid, and sticky bit, which grant
special privileges.\
• Access Control List (ACL): Provides more fine-grained permissions for
individual users or groups.

# Permission Values

Permissions are represented by numeric values:\
• Read (r): Value 4. Allows viewing a file\'s contents or listing a
directory\'s contents.\
• Write (w): Value 2. Allows modifying a file or creating/deleting files
within a directory.\
• Execute (x): Value 1. Allows running a script or accessing a
directory.

# User Categories

Permissions are defined for three categories of users:\
• User (u): The owner of the file.\
• Group (g): Users who belong to the file\'s group.\
• Others (o): All other users on the system.

# umask

The user file creation mode mask (umask) determines the default file
permissions for newly created files and directories. It acts as a
filter, masking out permission bits so that the final permissions are
more restrictive than the system-wide defaults.

When a new file or directory is created, the operating system starts
with a set of base permissions:\
• Files: 666 (read and write for owner, group, and others; no execute by
default)\
• Directories: 777 (read, write, and execute for owner, group, and
others)\
\
The umask value is subtracted from these base permissions to determine
the final permissions.

Default umask value is 0022

![](images/media/image1.png){width="3.8086636045494315in"
height="0.4167027559055118in"}

To change umask value permenantly for everyone use

#vi /etc/login.defs

![](images/media/image2.png){width="5.763194444444444in"
height="3.1979166666666665in"}

To change unmask value temperory

#umask (what permissions you want to give)

It will work until you reboot

![](images/media/image3.png){width="5.616666666666666in"
height="0.85in"}

# Methods to Set Permissions

Permissions can be set using:\
• Octal (Numeric) Method: Uses a three-digit number representing
permissions for user, group, and others. Example: 755 means rwx for
user, rx for group and others.\
• Symbolic Method: Uses letters (r, w, x) and symbols (+, -, =) to add,
remove, or set permissions. Example: u+rwx adds read, write, execute to
the user; g-w removes write from the group.

# Setting File and Directory Permissions in Linux

We can set permissions for files and directories in Linux using two
methods:

- 1\. Octal or Numeric Method (e.g., 421)

- 2\. Symbolic Method (e.g., rwx)

## Permission Values

Each permission has a specific numeric value:

• Read (r) = 4

• Write (w) = 2

• Execute (x) = 1

Example: rw rx wx = 6 5 3

## 1. Numeric (Octal) Method

In this method, permissions are represented using numbers that are the
sum of the permission values:\
\# chmod 744 \<file/directory\> -\> Owner: read, write, execute (7);
Group: read (4); Others: read (4)

![](images/media/image4.png){width="5.7659722222222225in"
height="0.2701388888888889in"}

![](images/media/image5.png){width="5.768055555555556in"
height="1.6152777777777778in"}

## 2. Symbolic Method

In this method, permissions are changed using letters to represent users
and permissions:\
\# chmod u=rwx,g=rw,o=r \<file/directory\> -\> User: read, write,
execute; Group: read, write; Others: read

It overwrites the permissions.

![](images/media/image6.png){width="5.767361111111111in"
height="0.35555555555555557in"}

![](images/media/image7.png){width="5.763194444444444in"
height="1.4743055555555555in"}

\# chmod u+x,g+rw,o+r \<file/directory\>

Its add permission to already existing one

![](images/media/image8.png){width="5.761111111111111in"
height="0.27152777777777776in"}

![](images/media/image9.png){width="5.761805555555555in"
height="1.6930555555555555in"}

#chmod u-r,g-x,o-w \<username\>

It removes the permission

![](images/media/image10.png){width="5.768055555555556in"
height="0.3541666666666667in"}

![](images/media/image11.png){width="5.763888888888889in"
height="1.9388888888888889in"}

\# chmod a=rwx testfile1 -\> Give read, write, execute to all (user,
group, others)

![](images/media/image12.png){width="5.7652777777777775in"
height="0.28194444444444444in"}

![](images/media/image13.png){width="5.7659722222222225in"
height="1.9236111111111112in"}

\+ → add permission\
- → remove permission\
= → set exact permission (replace existing)

# Commands for Managing Permissions and Ownership

Key commands to manage permissions and ownership include:\
• ls -l: Displays file permissions, ownership, and other details.\
• umask: Shows or sets the default permission mask for new files and
directories. Default is typically 0022.\
• chmod: Changes file and directory permissions.\
- Numeric: chmod 644 \<filename\>\
- Symbolic: chmod u=rwx,g=rw,o=r \<filename\>\
• chown: Changes file/directory ownership.\
- chown \<username\> \<filename\>

![](images/media/image14.png){width="5.761805555555555in"
height="0.34444444444444444in"}

![](images/media/image15.png){width="5.763888888888889in"
height="2.129861111111111in"}

\- chown -R \<username\> \<filename\> (to change recursive file)

![](images/media/image16.png){width="5.768055555555556in"
height="2.084722222222222in"}

• chgrp: Changes the group ownership of a file or directory.\
- chgrp \<groupname\> \<filename\>

![](images/media/image17.png){width="5.761805555555555in"
height="0.3055555555555556in"}

![](images/media/image18.png){width="5.767361111111111in"
height="0.3145833333333333in"}

![](images/media/image19.png){width="5.766666666666667in"
height="0.8291666666666667in"}

#chown :

It can also change group

![](images/media/image20.png){width="5.764583333333333in"
height="0.31527777777777777in"}

![](images/media/image21.png){width="5.759722222222222in"
height="2.301388888888889in"}

# Default Permissions

Default permissions vary by context:\
• Default directory permissions: 777 (read, write, execute for all).\
• Default file permissions: 666 (read and write for all, no execute).\
• Default permissions for / (root filesystem): 555 (read and execute for
all).\
• Default permissions for /root directory: 550 (owner read/execute,
group read/execute).\
• Default permissions for /home: 700 (owner full access, no access for
others).\
• Default permissions for /var/spool/mail: 660 (owner and group
read/write).
