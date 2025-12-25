# Access Control List (ACL)

An Access Control List (ACL) is a set of rules that define which users
or groups have what kind of access (read, write, execute) to a specific
file or directory. ACLs provide more fine-grained permission management
than the standard owner-group-other permission model.

## Verify the Default ACL on a File/Folder

To check the default ACL settings of a file or directory, use the
command:\
getfacl \<file/foldername\>

![](images/media/image1.png){width="5.7625in"
height="0.26944444444444443in"}

![](images/media/image2.png){width="4.875in" height="2.05in"}

## Set ACL on a File for a Specific User

Use setfacl with the -m (modify) option to assign permissions to a
specific user:\
setfacl -m u:username:rwx filename

![](images/media/image3.png){width="5.761805555555555in"
height="2.0527777777777776in"}

setfacl -m u:username:7 filename\
The \'rwx\' or \'7\' represents read, write, and execute permissions.

## Set ACL on a File for a Specific Group

Similarly, you can assign ACL permissions to a group:\
setfacl -m g:groupname:rwx filename

![](images/media/image4.png){width="5.768055555555556in"
height="0.29930555555555555in"}

![](images/media/image5.png){width="5.7625in" height="4.175in"}

setfacl -m g:groupname:7 filename

## Remove ACL for a Specific User

To remove ACL permissions for a particular user:\
setfacl -x u:username /path/to/file_or_directory

![](images/media/image6.png){width="5.764583333333333in"
height="2.232638888888889in"}

## Remove ACL for a Specific Group

To remove ACL permissions for a specific group:\
setfacl -x g:groupname /path/to/file_or_directory

![](images/media/image7.png){width="5.767361111111111in"
height="5.040972222222222in"}

## Remove All ACLs

To remove all ACL entries from a file or directory:\
\# setfacl -b file_or_directory

![](images/media/image8.png){width="5.058333333333334in"
height="2.225in"}

![](images/media/image9.png){width="5.533333333333333in"
height="2.3583333333333334in"}

![](images/media/image10.png){width="5.516666666666667in"
height="2.4166666666666665in"}

This command clears all ACLs, reverting to the standard Linux permission
system.

## Additional Examples

Recursive Operations:\
getfacl -R /secure \# Recursively list ACLs

![](images/media/image11.png){width="5.767361111111111in"
height="1.9861111111111112in"}

To remove Recursively ACLs

\# setfacl -R -b u:username: filename \# Recursively ACLs

![](images/media/image12.png){width="5.763888888888889in"
height="4.113888888888889in"}
