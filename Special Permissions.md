**Special Permissions in Linux**

Special permissions in Linux provide additional security and control for
files and directories beyond the standard read, write, and execute
permissions. They include Setuid, Setgid, and Sticky Bit.

## Types of Special Permissions

1\. Setuid (SUID) - Numeric value: 4\
2. Setgid (SGID) - Numeric value: 2\
3. Sticky Bit - Numeric value: 1

## Permission Symbol Representation

Below are the symbolic representations for these special permissions:\
suid sgid stickybit\
rwx r-x r-x\
s s t\
rws r-s r-t\
rwS r-S r-T

## 1. Setuid (SUID)

Set User ID (Setuid) allows a user to execute a file with the
permissions of the file owner. This is commonly used for executable
files requiring temporary elevated privileges.\
\
Commands to manage Setuid:\
• Set: chmod 4755 \<filename\>

![](images/media/image1.png){width="5.763888888888889in"
height="0.27847222222222223in"}

![](images/media/image2.png){width="5.763194444444444in"
height="2.175in"}

To remove permission:

#chmod 0755 \<file name\>

![](images/media/image3.png){width="5.7659722222222225in"
height="2.7180555555555554in"}

• Symbolic: chmod u+s \<filename\>

![](images/media/image4.png){width="5.760416666666667in"
height="0.2604166666666667in"}

![](images/media/image5.png){width="5.7652777777777775in"
height="2.4555555555555557in"}

• Remove: chmod u-s \<filename\>

![](images/media/image6.png){width="5.761111111111111in"
height="2.7118055555555554in"}

## 2. Setgid (SGID)

Set Group ID (Setgid) behaves similarly to Setuid, but it sets the
process\'s effective group ID to that of the file\'s group owner,
granting group-based permissions.\
\
On Files:\
• Set: chmod 2755 \<file\>

![](images/media/image7.png){width="5.761805555555555in"
height="0.28958333333333336in"}

![](images/media/image8.png){width="5.763194444444444in"
height="3.0743055555555556in"}

To remove

#chmod 0755 \<file name\>

![](images/media/image9.png){width="5.767361111111111in"
height="2.93125in"}

• Symbolic: chmod g+s \<file\>

![](images/media/image10.png){width="5.761805555555555in"
height="0.3590277777777778in"}

![](images/media/image11.png){width="5.761805555555555in"
height="3.140972222222222in"}

• Remove: chmod g-s \<file\>

![](images/media/image12.png){width="5.7659722222222225in"
height="3.1479166666666667in"}

On Directories:\
When SGID is set on a directory, all new files or subdirectories inside
inherit the directory\'s group ownership.

• Set: chmod 2755 \<directory\>\
• Symbolic: chmod g+s \<directory\>

![](images/media/image13.png){width="5.763888888888889in"
height="0.2833333333333333in"}

![](images/media/image14.png){width="5.763888888888889in"
height="3.373611111111111in"}

• Remove: chmod g-s \<directory\>

![](images/media/image15.png){width="5.768055555555556in"
height="3.3569444444444443in"}

To remove or add directories with recursive files

#chmod -R \<dir name\>

![](images/media/image16.png){width="5.7625in"
height="0.24861111111111112in"}

![](images/media/image17.png){width="5.7659722222222225in"
height="3.5701388888888888in"}

## 3. Sticky Bit

The Sticky Bit ensures that only the file owner or root can delete or
rename a file within a directory, even if others have write permissions
to the directory. It\'s often used on public directories like /tmp.\
\
Commands to manage Sticky Bit:

• Set: chmod 1755 \<file/directory\>

![](images/media/image18.png){width="5.767361111111111in"
height="0.2604166666666667in"}

![](images/media/image19.png){width="5.7625in"
height="3.7631944444444443in"}

To remove

#chmod 0755 \<dirname\>

![](images/media/image20.png){width="5.763194444444444in"
height="3.7131944444444445in"}

• Symbolic: chmod o+t \<file/directory\>

![](images/media/image21.png){width="5.763194444444444in"
height="3.7305555555555556in"}

• Remove: chmod o-t \<file/directory\>

![](images/media/image22.png){width="5.767361111111111in"
height="3.74375in"}
