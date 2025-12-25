# User and Group Management in Linux

Linux provides powerful tools for managing users and groups. This
document explains how to create groups, add users, manage group
memberships, delete groups, and check user password status.

## Creating Groups

To create a new group, use the command:

Groupadd \[groupname\]

![](images/media/image1.png){width="5.591666666666667in"
height="0.675in"}

![](images/media/image2.png){width="1.9666666666666666in"
height="0.425in"}

This creates a new group with the specified name. A unique Group ID
(GID) will be assigned automatically. To verify that the group was
created, check the /etc/group file.

Example:

cat /etc/group /grep \[groupname\]

## Adding a User to a Group

To add a user to a secondary group, you can use either of these
commands:

gpasswd -a\[username\] \[groupname\]

![](images/media/image3.png){width="5.764583333333333in"
height="0.5451388888888888in"}

usermod -aG \[groupname\]

\[username\]

![](images/media/image4.png){width="5.7659722222222225in"
height="2.848611111111111in"}

Explanation:

\- The \'gpasswd -a\' command adds the user to the specified group.\
- The \'usermod -aG\' command adds the user to one or more secondary
groups.\
- The \'-G\' option specifies secondary groups, while the \'-g\' option
is used for the primary group.

## Removing a User from a Group

To remove a user from a group, use the command:

gpasswd -d \[username\] \[groupname\]

![](images/media/image5.png){width="5.761805555555555in"
height="0.5694444444444444in"}

This removes the user from the specified group. The user will still
remain in their primary group.

## Deleting a Group

To delete a group, use the command:

groupdel \[groupname\]

![](images/media/image6.png){width="5.533333333333333in"
height="7.283333333333333in"}

![](images/media/image7.png){width="3.8in"
height="2.8916666666666666in"}

This deletes the group. However, if the group is the primary group of a
user, it cannot be deleted. You must first change the user's primary
group before deletion.

## Checking Password Status

To check the password status for a user, use the command:

passwd -S \[username\]

![](images/media/image8.png){width="5.761805555555555in"
height="0.5347222222222222in"}

This displays information about the user's password status. The output
includes a code indicating the password state:

- \* PS: Password is set.\
  \* PL: Password is locked.\
  \* NP: No password is set.
