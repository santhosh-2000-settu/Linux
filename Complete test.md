#  Linux Module 1 Exercise 

## 1. Creating Users in Linux

• Which command is used to create a new user in Linux?

The \`useradd\` command is used to create a new user in Linux.

![](images/media/image1.tmp){width="2.437625765529309in"
height="0.5416940069991251in"}

• What is the syntax for creating a user using the useradd command?

Syntax: \`useradd \[options\] username\`\
Example: \`useradd john\`

![](images/media/image2.tmp){width="2.368176946631671in"
height="0.5555839895013124in"}

• Can you create a user with specific user ID (UID) and group ID (GID)
using the useradd command? If yes, how?

Yes. Use the \`-u\` option for UID and \`-g\` for GID.\
Example: \`useradd -u 1050 -g 100 denis\`

![](images/media/image3.tmp){width="4.062708880139983in"
height="0.5833628608923884in"}

• How can you set an initial password for a newly created user?

Use the \`passwd\` command.\
Example: \`passwd denis\`

![](images/media/image4.tmp){width="4.6738517060367455in"
height="1.090333552055993in"}

• What happens if you try to create a user with a username that already
exists on the system?

The system will display an error message: \`useradd: user \'username\'
already exists\`.

![](images/media/image5.tmp){width="3.118216316710411in"
height="0.38890857392825895in"}

• Is it possible to create a user without a home directory? If yes, how?

Yes, use the \`-M\` option.\
Example: \`useradd -M wright\`

![](images/media/image6.tmp){width="2.9515409011373577in"
height="0.2222331583552056in"}

![](images/media/image7.tmp){width="2.368176946631671in"
height="0.37501968503937005in"}

• How can you specify the shell for a user during creation?

Use the \`-s\` option.\
Example: \`useradd -s /bin/bash noe\`

![](images/media/image8.tmp){width="6.0in" height="2.047222222222222in"}

• Can you create a user with additional supplementary groups using the
useradd command? If yes, how?

Yes, use the \`-G\` option.\
Example: \`useradd -G wheel,developers fincher\`

• How can you verify that a user has been successfully created?

You can check \`/etc/passwd\` file or use \`id username\` or \`getent
passwd username\`.

![](images/media/image9.tmp){width="3.791861329833771in"
height="0.4027985564304462in"}

• Is there a way to create a user with a specific expiration date? If
yes, how?

Yes, use the \`-e\` option.\
Example: \`useradd -e 2025-12-31 eric

![](images/media/image10.tmp){width="3.7224136045494314in"
height="0.38196412948381453in"}

![](images/media/image11.tmp){width="2.7987554680664917in"
height="0.2083442694663167in"}

![](images/media/image12.tmp){width="2.645968941382327in"
height="0.38196412948381453in"}

## 2. cat command in Linux

• What is the purpose of the cat command in Linux?

The \`cat\` command is used to display, combine, and create files.

![](images/media/image13.tmp){width="2.1459437882764654in"
height="0.39585411198600173in"}

• How do I use the cat command to display the contents of a file on the
terminal?

Use \`cat filename\`. Example: \`cat /etc/passwd\`

![](images/media/image14.tmp){width="6.0in"
height="3.672222222222222in"}

• Can cat display the contents of multiple files at once?

Yes. Example: \`cat file1 file2\`

![](images/media/image15.tmp){width="2.9237609361329833in"
height="0.9306036745406824in"}

• What are some options available with the cat command, and how do I use
them?

\`-n\` (number lines), \`-b\` (number non-empty lines), \`-s\` (suppress
blank lines). Example: \`cat -n file\`

• How can I create a new file using the cat command?

Use \`cat \> filename\` and press Ctrl+D to save.

![](images/media/image16.tmp){width="3.4237871828521436in"
height="0.8542104111986002in"}

• Is it possible to concatenate multiple files using cat? If yes, how?

Yes. Example: \`cat file1 file2 \> combined.txt\`

![](images/media/image17.tmp){width="6.0in"
height="2.095138888888889in"}

• How does the cat command handle binary files?

\`cat\` can display binary data, but output may contain unreadable
characters.

![](images/media/image18.tmp){width="4.396059711286089in"
height="0.6736461067366579in"}

• Can I number the lines while displaying the contents of a file with
cat?

Yes, use \`cat -n filename\`.

![](images/media/image19.tmp){width="2.6737489063867015in"
height="1.7709241032370953in"}

• How do I suppress the display of trailing whitespace in cat output?

\`cat\` does not natively support this; use tools like \`sed\` or
\`awk\`.

• Can I use cat to append the contents of one file to another?

Yes. Example: \`cat file1 \>\> file2\`

![](images/media/image20.tmp){width="3.2501673228346455in"
height="2.0903849518810147in"}

• Is it possible to create a copy of a file using the cat command?

Yes. Example: \`cat file1 \> file2\`

![](images/media/image21.tmp){width="2.5765212160979876in"
height="0.4653018372703412in"}

• How can I use cat to display non-printing characters like tabs and
newlines as visible characters?

Use \`cat -v filename\`.

![](images/media/image22.tmp){width="3.0348786089238846in"
height="0.6111428258967629in"}

• What happens if I use cat with multiple files, but some of them do not
exist?

\`cat\` will display an error message for missing files but continue
with others.

![](images/media/image23.tmp){width="4.2363287401574805in"
height="1.854261811023622in"}

• Can cat be used to view the contents of remote files over SSH?

Yes, by combining with SSH. Example: \`ssh user@host cat /path/to/file\`

• How does the cat command handle files with very long lines?

\`cat\` displays them as-is, wrapping may depend on the terminal
settings.

## 3. "ls" command in Linux

• What is the purpose of the ls command in Linux?

The \`ls\` command lists files and directories.

![](images/media/image24.tmp){width="6.0in" height="0.30625in"}

• How do I use the ls command to list files and directories in the
current directory?

Use \`ls\`.

![](images/media/image25.tmp){width="6.0in"
height="0.3104166666666667in"}

• Can ls display file and directory details, such as permissions, owner,
size, and modification date?

Yes, use \`ls -l\` for long listing format.

![](images/media/image26.tmp){width="5.521116579177603in"
height="2.8473687664041996in"}

• How can I list files and directories in a specific directory other
than the current one?

Use \`ls /path/to/directory\`.

![](images/media/image27.tmp){width="2.6112456255468066in"
height="0.4027985564304462in"}

• What are some common options that can be used with the ls command, and
how do I use them?

\`-a\` (show hidden), \`-l\` (long list), \`-h\` (human readable),
\`-R\` (recursive).

![](images/media/image28.tmp){width="6.0in"
height="0.5305555555555556in"}

![](images/media/image29.tmp){width="5.5697309711286085in"
height="2.8404232283464568in"}

![](images/media/image30.tmp){width="6.0in"
height="1.5840277777777778in"}

![](images/media/image31.tmp){width="6.0in"
height="0.3298611111111111in"}

• How can I make ls show hidden files and directories?

Use \`ls -a\`.

![](images/media/image32.tmp){width="6.0in"
height="0.5111111111111111in"}

- • Is it possible to list files and directories in a long format with
  human-readable file sizes?

Yes, use \`ls -lh\`.

![](images/media/image33.tmp){width="5.548896544181977in"
height="2.8404232283464568in"}

• How do I sort the ls output by different criteria, such as name, size,
or modification time?

Use \`\--sort=size\`, \`\--sort=time\`, or \`\--sort=name\`.

![](images/media/image34.tmp){width="6.0in"
height="0.30972222222222223in"}

• Can ls display files and directories with color-coded output?

Yes, use \`ls \--color=auto\`.

![](images/media/image35.tmp){width="6.0in"
height="0.31805555555555554in"}

• How can I recursively list files and directories within
sub-directories?

Use \`ls -R\`.

![](images/media/image36.tmp){width="2.6876377952755908in"
height="0.6319772528433946in"}

• What is the difference between ls and ls -l in terms of the
information they display?

\`ls\` shows names only; \`ls -l\` shows detailed info like permissions
and size.

![](images/media/image37.tmp){width="6.0in" height="0.325in"}

• How can I use ls to find files that match a specific pattern or
extension?

Use wildcards. Example: \`ls \*.txt\`

![](images/media/image38.tmp){width="3.159884076990376in"
height="0.8333759842519685in"}

• Can ls display file sizes in units other than bytes, such as kilobytes
or megabytes?

Yes, use \`ls -lh\` for human-readable sizes.

![](images/media/image39.tmp){width="5.562785433070866in"
height="3.50712489063867in"}

• How do I use ls to list only directories, excluding regular files?

Use \`ls -d \*/\`

![](images/media/image40.tmp){width="2.639024496937883in"
height="0.6944805336832895in"}

• What happens if I use ls with a directory that I don't have permission
to access?

\`ls\` will display a \'Permission denied\' message for that directory.

![](images/media/image41.tmp){width="6.0in"
height="2.984027777777778in"}

## 4. Creating Directories in Linux

• Which command is used to create a new directory in Linux?

The \`mkdir\` command.

![](images/media/image42.tmp){width="6.0in" height="0.76875in"}

• What is the syntax for creating a directory using the mkdir command?

Syntax: \`mkdir \[options\] directory_name\`

![](images/media/image42.tmp){width="6.0in" height="0.76875in"}

• Can you create multiple directories at once using the mkdir command?
If yes, how?

Yes. Example: \`mkdir dir1 dir2 dir3\`

![](images/media/image43.tmp){width="6.0in"
height="0.6388888888888888in"}

• How can you specify the full path for creating a directory in a
specific location?

Use the full path. Example: \`mkdir /home/user/newdir\`

![](images/media/image44.tmp){width="4.375225284339457in"
height="1.0208858267716536in"}

• What happens if you try to create a directory with a name that already
exists in the current location?

The system shows an error: \`mkdir: cannot create directory: File
exists\`.

![](images/media/image45.tmp){width="5.4030555555555555in"
height="0.6597561242344707in"}

• Is it possible to create a directory with a space in its name? If yes,
how?

No it will create to directories

![](images/media/image46.tmp){width="6.0in"
height="0.5583333333333333in"}

• How can you verify that a directory has been successfully created?

Use \`ls\` or \`ls -l\` to check if it exists.

![](images/media/image47.tmp){width="6.0in" height="0.63125in"}

• Is there a way to create directories with specific permissions using
the mkdir command?

Yes, use the \`-m\` option. Example: \`mkdir -m 755 newdir\`

![](images/media/image48.tmp){width="5.528062117235345in"
height="5.062760279965004in"}

• How can you create nested directories (directories within directories)
using the mkdir command?

Use the \`-p\` option. Example: \`mkdir -p parent/child/grandchild\`

![](images/media/image49.tmp){width="5.451668853893263in"
height="2.069550524934383in"}

• Can you create a directory with a relative path instead of an absolute
path? If yes, how?

Yes. Example: \`mkdir ../newdir\` creates it relative to the current
directory.

L

![](images/media/image50.tmp){width="6.0in"
height="0.5361111111111111in"}

### 5. Copy (cp) Command

- • How do I copy a file to a different directory using the cp command?

Example: \`cp file1 /home/user/Documents/\`

![](images/media/image51.tmp){width="4.277997594050744in"
height="1.0556102362204725in"}

- • Can I preserve the original file permissions when copying with cp?

Yes, use \`cp -p file1 /path/\`

![](images/media/image52.tmp){width="5.847522965879265in"
height="1.826482939632546in"}

- • How can I copy multiple files at once using the cp command?

Example: \`cp file1 file2 file3 /destination/\`

![](images/media/image53.tmp){width="5.528062117235345in"
height="1.8403718285214348in"}

• Is it possible to overwrite an existing file when copying with cp?

Yes, by default cp overwrites files. Use \`-i\` to prompt before
overwrite.

![](images/media/image54.tmp){width="5.528062117235345in"
height="0.4236329833770779in"}

• How can I copy a directory and its contents using cp?

Use the \`-r\` option. Example: \`cp -r dir1 /backup/\`

![](images/media/image55.tmp){width="6.0in"
height="2.3944444444444444in"}

### Move (mv) Command

• How do I move a file to a different directory using the mv command?

Example: \`mv file1 /home/user/Documents/\`

![](images/media/image56.tmp){width="3.9724267279090113in"
height="1.0139413823272092in"}

• Can I rename a file while moving it with the mv command?

Yes. Example: \`mv oldname.txt newname.txt\`

![](images/media/image57.tmp){width="6.0in" height="1.2in"}

• What happens if I move a file to a directory where a file with the
same name already exists?

It overwrites the existing file unless \`-i\` is used.

![](images/media/image58.tmp){width="3.5140693350831147in"
height="0.8055971128608924in"}

• How can I move multiple files at once using the mv command?

Example: \`mv file1 file2 /destination/\`

![](images/media/image59.tmp){width="3.777972440944882in"
height="0.26390201224846893in"}

![](images/media/image60.tmp){width="2.9237609361329833in"
height="0.638921697287839in"}

• Is it possible to move a directory and its contents using mv?

Yes. Example: \`mv dir1 /newpath/\`

![](images/media/image61.tmp){width="3.896033464566929in"
height="0.8542104111986002in"}

### Remove (rm) Command

• How do I remove a file using the rm command?

Example: \`rm file1\`

![](images/media/image62.tmp){width="4.166881014873141in"
height="1.250064523184602in"}

• Can I remove multiple files at once using the rm command?

Yes. Example: \`rm file1 file2 file3\`

![](images/media/image63.tmp){width="4.027984470691163in"
height="1.465353237095363in"}

• How can I remove a directory and its contents using the rm command?

Use \`rm -r directory_name\`

![](images/media/image64.tmp){width="4.159935476815398in"
height="0.5972528433945756in"}

• What happens if I try to remove a file that is write-protected or has
special permissions?

You cant it will show permission denied

![](images/media/image65.tmp){width="6.0in" height="2.96875in"}

![](images/media/image66.tmp){width="5.014146981627297in"
height="1.4028499562554682in"}

• Is there a way to force the removal of files or directories using rm?

Yes, use \`rm -rf directory_name\`

![](images/media/image67.tmp){width="4.125212160979878in"
height="0.888934820647419in"}

# 6. File & Directory Permissions

- What are the three basic permissions for a file in Linux?

Read (r), Write (w), and Execute (x).

![](images/media/image68.tmp){width="4.597458442694663in"
height="0.32640529308836397in"}

- How are file permissions represented in the output of the ls -l
  command?

As a 10-character string (e.g., -rw-r\--r\--).

![](images/media/image68.tmp){width="4.597458442694663in"
height="0.32640529308836397in"}

- What does the \'r\' permission indicate for a file? What about \'w\'
  and \'x\'?

\'r\' = read, \'w\' = write, \'x\' = execute.

- How can you change the permissions of a file using the chmod command?

Use chmod followed by permission and filename (e.g., chmod 755 file).

![](images/media/image69.tmp){width="5.014146981627297in"
height="0.9931069553805775in"}

![](images/media/image70.tmp){width="5.576675415573053in"
height="4.069653324584427in"}

![](images/media/image71.tmp){width="4.944698162729659in"
height="0.6458661417322835in"}

- What does the numeric representation 644 mean in terms of file
  permissions?

Owner: read/write, Group: read, Others: read.

- How can you change the permissions of a directory in Linux?

Use chmod with directory name (e.g., chmod 755 dir).

![](images/media/image72.tmp){width="4.646071741032371in"
height="0.3125164041994751in"}

![](images/media/image73.tmp){width="5.5558409886264215in"
height="1.6389730971128609in"}

- What does the \'x\' permission mean for a directory?

It allows entering or accessing files inside the directory.

- How do you recursively change the permissions of all files and
  directories within a directory?

Use chmod -R option (e.g., chmod -R 755 dir).

![](images/media/image74.tmp){width="3.896033464566929in"
height="1.6111942257217848in"}

- What is the difference between the chmod command and the chown
  command?

chmod changes permissions; chown changes ownership.

- How can you check the permissions of a directory using the ls command?

Use ls -ld directory_name.

![](images/media/image75.tmp){width="4.500230752405949in"
height="0.4653018372703412in"}

# 7. Vi Editor in Linux

- What is the purpose of the Vi editor in Linux?

To create and edit text files.

- What is the command to open a file in Vi for editing?

vi filename

![](images/media/image76.tmp){width="3.930757874015748in"
height="0.798652668416448in"}

![](images/media/image77.tmp){width="6.0in"
height="5.4215277777777775in"}

- How do you switch to insert mode in Vi to start adding or modifying
  text?

Press \'i\' in normal mode.

![](images/media/image78.tmp){width="4.166881014873141in"
height="5.882246281714786in"}

- How do you save changes and exit Vi?

Press :wq and Enter.

![](images/media/image78.tmp){width="4.166881014873141in"
height="5.882246281714786in"}

- What is the command to exit Vi without saving changes?

Press :q! and Enter.

![](images/media/image79.tmp){width="3.5765726159230096in"
height="5.847522965879265in"}

- How can you move the cursor to the beginning and end of a line in Vi?

Use 0 for beginning, \$ for end.

![](images/media/image80.tmp){width="2.15288823272091in"
height="0.7708727034120735in"}

- What is the command to search for a specific word or pattern in Vi?

Use /word and press Enter.

![](images/media/image81.tmp){width="2.5209623797025373in"
height="5.305827865266842in"}

- How can you delete a character or a line in Vi?

x deletes a char; dd deletes a line.

![](images/media/image82.tmp){width="2.1112193788276468in"
height="1.0694991251093613in"}

![](images/media/image83.tmp){width="2.166778215223097in"
height="1.1389479440069992in"}

- How do you copy and paste text in Vi?

yy copies a line; p pastes it.

![](images/media/image84.tmp){width="0.9861614173228347in"
height="1.0486646981627297in"}

- What are some basic navigation commands in Vi to move between
  sections?

h, j, k, l for left, down, up, right; G to end, gg to top.

- How do you search for a specific word or phrase in Vi?

Use / followed by the word.

![](images/media/image85.tmp){width="3.604351487314086in"
height="5.312773403324584in"}

- What is the difference between the :w and :wq commands in Vi?

:w saves only; :wq saves and quits.

- How do you delete a single character in normal mode?

Use x key.

# 8. Special Permissions in Linux

- What are the three special permissions in Linux?

setuid, setgid, and sticky bit.

- What is the purpose of the setuid permission?

Allows users to run an executable with the file owner\'s privileges.

- How is the setuid permission represented in the output of the ls -l
  command?

Shown as \'s\' in the user's execute field (e.g., -rwsr-xr-x).

![](images/media/image86.tmp){width="4.166881014873141in"
height="0.34723972003499565in"}

- What is the effect of the setuid permission on an executable file?

It runs with the owner\'s privileges instead of the user\'s.

- What is the purpose of the setgid permission?

Ensures files created in a directory inherit the group ownership.

- How is the setgid permission represented in the output of the ls -l
  command?

Shown as \'s\' in the group's execute field (e.g., drwxr-sr-x).

![](images/media/image87.tmp){width="4.743299431321085in"
height="0.2986264216972878in"}

- What is the effect of the setgid permission on a directory?

Files inherit the directory\'s group ownership.

- What is the purpose of the sticky bit permission?

Prevents users from deleting others\' files in shared directories.

- How is the sticky bit permission represented in the output of the ls
  -l command?

Shown as \'t\' in the others' execute field (e.g., drwxrwxrwt).

![](images/media/image88.tmp){width="5.5697309711286085in"
height="2.215391513560805in"}

![](images/media/image89.tmp){width="5.180821303587051in"
height="1.0556102362204725in"}

- What is the significance of the sticky bit on a directory?

Only the file owner or root can delete files inside it.

# 9. User and Group Administration in Linux

- What is the command to create a new user in Linux?

useradd username

![](images/media/image90.tmp){width="2.9515409011373577in"
height="0.6458661417322835in"}

- How can you specify a user\'s home directory during user creation?

useradd -d /home/dirname username

![](images/media/image91.tmp){width="5.0974846894138235in"
height="0.5000251531058618in"}

- How do you assign a password to a user account in Linux?

passwd username

![](images/media/image92.tmp){width="5.437779965004374in"
height="1.465353237095363in"}

- What command is used to delete a user from the system?

userdel username

![](images/media/image93.tmp){width="2.9932097550306214in"
height="0.4375229658792651in"}

- How can you add an existing user to a specific group?

usermod -aG groupname username

![](images/media/image94.tmp){width="4.521065179352581in"
height="0.25001312335958004in"}

- What command is used to create a new group in Linux?

groupadd groupname

![](images/media/image95.tmp){width="3.3612839020122482in"
height="2.6876377952755908in"}

![](images/media/image96.tmp){width="1.8750962379702538in"
height="0.6250317147856518in"}

- How do you add a user to a newly created group?

usermod -aG groupname username

![](images/media/image94.tmp){width="4.521065179352581in"
height="0.25001312335958004in"}

- What is the purpose of the chgrp command?

Changes the group ownership of a file.

- How can you list all the users on a Linux system?

View /etc/passwd file or use getent passwd.

![](images/media/image97.tmp){width="6.0in"
height="3.870138888888889in"}

- What command can you use to modify a user's account settings?

usermod command.

- How can you assign a user to a specific group during user creation?

useradd -G groupname username

![](images/media/image98.tmp){width="4.548845144356956in"
height="2.9654297900262465in"}

![](images/media/image99.tmp){width="3.2987806211723534in"
height="1.0000513998250218in"}

- What is the purpose of the usermod command?

Modifies user account details.

- How do you change a user\'s password in Linux?

passwd username

![](images/media/image100.tmp){width="5.396111111111111in"
height="1.437574365704287in"}

- How do you lock or unlock a user account using the passwd command?

passwd -l username (lock), passwd -u username (unlock).

![](images/media/image101.tmp){width="3.5279593175853017in"
height="1.4097944006999126in"}

- What is the purpose of the groupadd command?

Creates a new group.

- How can you remove a user from a group?

gpasswd -d username groupname.

![](images/media/image102.tmp){width="4.597458442694663in"
height="1.4792432195975502in"}

- What command is used to delete a user account in Linux?

userdel username.

![](images/media/image103.tmp){width="3.312670603674541in"
height="0.8542104111986002in"}

- How do you display details of a specific user?

Use id or finger username.

![](images/media/image104.tmp){width="4.354390857392826in"
height="0.4444674103237095in"}

- What is the difference between useradd and adduser commands?

useradd is low-level; adduser is a friendly interactive script.

- What is the purpose of the /etc/passwd file in Linux?

Stores user account information.

![](images/media/image105.tmp){width="6.0in"
height="3.3305555555555557in"}

- What is the purpose of the /etc/shadow file?

Stores encrypted passwords and password policies.

![](images/media/image106.tmp){width="6.0in"
height="2.504861111111111in"}

- What is the purpose of the /etc/gshadow file?

Stores group password and admin information.

![](images/media/image107.tmp){width="3.354339457567804in"
height="4.882194881889764in"}

- What is the purpose of the /etc/group file?

Defines groups and their members.

![](images/media/image108.tmp){width="3.1529396325459316in"
height="4.958588145231846in"}

- How can you view the contents of these files?

Use cat, less, or more commands.

![](images/media/image109.tmp){width="3.2987806211723534in"
height="0.25001312335958004in"}

# 10. Processes in Linux

- What is a process in Linux?

An instance of a running program.

- How can you view the currently running processes?

Use ps, top, or htop commands.

![](images/media/image110.tmp){width="3.5279593175853017in"
height="3.4237871828521436in"}

![](images/media/image111.tmp){width="2.6251345144356955in"
height="0.2222331583552056in"}

![](images/media/image112.tmp){width="6.0in"
height="3.192361111111111in"}

- What command is used to start a new process?

Run the program or script name directly.

![](images/media/image113.tmp){width="6.0in"
height="0.4736111111111111in"}

- How can you identify the process ID (PID)?

Use ps or pgrep command.

![](images/media/image114.tmp){width="3.465456036745407in"
height="4.048818897637795in"}

![](images/media/image115.tmp){width="2.5765212160979876in"
height="0.2708475503062117in"}

- What is the purpose of the ps command?

Displays running processes and their status.

![](images/media/image116.tmp){width="3.604351487314086in"
height="3.2640562117235348in"}

![](images/media/image115.tmp){width="2.5765212160979876in"
height="0.2708475503062117in"}

- How can you terminate a process?

Use kill or killall command.

![](images/media/image117.tmp){width="2.9098720472440944in"
height="0.3055708661417323in"}

- What is the difference between a foreground and background process?

Foreground runs interactively; background runs detached.

- How do you start a process in the background?

Append \'&\' at the end of the command.

![](images/media/image118.tmp){width="2.9237609361329833in"
height="0.4375229658792651in"}

- How can you check the status of a process?

Use ps or top command.

![](images/media/image119.tmp){width="6.0in"
height="3.191666666666667in"}

- What is a parent process and a child process?

Parent spawns child processes.

- How can you change the priority of a process?

Use nice or renice command.

![](images/media/image120.tmp){width="4.854416010498688in"
height="0.4305774278215223in"}

- What is the purpose of the top command?

Monitors real-time system processes and resource usage.

![](images/media/image121.tmp){width="6.0in"
height="3.1944444444444446in"}

- How can you monitor resource usage of a process?

Use top, or ps aux.

![](images/media/image122.tmp){width="6.0in"
height="2.452777777777778in"}

- What are the common process states?

Running, Sleeping, Zombie, Stopped.

- How can you send signals to a process?

Use kill -SIGNAL PID (e.g., kill -9 PID).

- How do I run the top command?

Type top in terminal.

![](images/media/image123.tmp){width="6.0in"
height="3.248611111111111in"}

- What information does top display?

CPU, memory, PID, user, and command info.

![](images/media/image123.tmp){width="6.0in"
height="3.248611111111111in"}

- How do I interpret CPU usage in top?

Shows CPU usage percentage for each process.

- How can I sort processes in top?

Press \'P\' for CPU, \'M\' for memory.

![](images/media/image124.tmp){width="6.0in"
height="3.1819444444444445in"}

![](images/media/image125.tmp){width="6.0in"
height="3.2465277777777777in"}

- Can I change update frequency in top?

Yes, press \'d\' and set the delay time.

![](images/media/image126.tmp){width="6.0in"
height="1.8006944444444444in"}

- How can I view processes of a specific user?

Use top -u username.

![](images/media/image127.tmp){width="3.014044181977253in"
height="0.2916819772528434in"}

![](images/media/image128.tmp){width="6.0in"
height="1.2604166666666667in"}

- Can top show full command line for each process?

Yes, press \'c\' key.

![](images/media/image129.tmp){width="6.0in"
height="3.178472222222222in"}

- How do I kill a process directly from top?

Press \'k\' then enter the PID.

![](images/media/image130.tmp){width="6.0in"
height="1.1701388888888888in"}

- Can top show overall system summary?

Yes, at the top section of the display.

![](images/media/image131.tmp){width="6.0in"
height="0.8548611111111111in"}

- How can I save top output to a file?

Use top -b -n 1 \> file.txt.

![](images/media/image132.tmp){width="6.0in"
height="3.2631944444444443in"}

## 11. Services in Linux

- What is a service in the context of Linux?

A service is a background process that performs specific system
functions, often managed by systemd.

- How can you check the status of a service in Linux?

Use \'systemctl status service_name\'.

![](images/media/image133.tmp){width="6.0in"
height="3.189583333333333in"}

- What command is used to start a service in Linux?

Use \'systemctl start service_name\'.

![](images/media/image134.tmp){width="6.0in"
height="2.527083333333333in"}

- How can you stop a running service in Linux?

Use \'systemctl stop service_name\'.

![](images/media/image135.tmp){width="6.0in"
height="2.472916666666667in"}

- What is the purpose of the systemctl command in Linux?

It controls and manages systemd services and units.

- How can you enable a service to start automatically at system boot in
  Linux?

Use \'systemctl enable service_name\'.

![](images/media/image136.tmp){width="4.014095581802275in"
height="0.25001312335958004in"}

![](images/media/image137.tmp){width="6.0in"
height="3.4631944444444445in"}

- What is the difference between a system service and a user service in
  Linux?

System services run for all users; user services run in a user\'s
session.

- How can you restart a service in Linux?

Use \'systemctl restart service_name\'.

![](images/media/image138.tmp){width="3.896033464566929in"
height="0.4305774278215223in"}

- What command is used to view the list of available services in Linux?

Use \'systemctl list-units \--type=service\'.

![](images/media/image139.tmp){width="6.0in"
height="2.673611111111111in"}

- How can you configure the behavior and settings of a service in Linux?

Edit its configuration file in /etc/systemd/system or use override
files.

![](images/media/image140.tmp){width="4.034930008748907in"
height="0.33335083114610675in"}

![](images/media/image141.tmp){width="6.0in"
height="2.6805555555555554in"}

- What is the purpose of the /etc/init.d directory in Linux?

It contains legacy SysV-style service scripts.

- How can you create a custom service in Linux?

By creating a .service file in /etc/systemd/system and enabling it with
systemctl.

- How can you check the logs and debug a service in Linux?

Use \'journalctl -u service_name\'.

![](images/media/image142.tmp){width="6.0in"
height="2.1805555555555554in"}

- What is the significance of service dependencies in Linux?

They define which services must start before or after another service.

## 12. Archiving and Transferring Files in Linux

- What command is used to create a tar archive of files and directories
  in Linux?

Use \'tar -cvf archive.tar files\'.

![](images/media/image143.tmp){width="5.81974300087489in"
height="3.041823053368329in"}

![](images/media/image144.tmp){width="5.298883420822397in"
height="1.604248687664042in"}

- How can you extract files from a tar archive in Linux?

Use \'tar -xvf archive.tar\'.

![](images/media/image145.tmp){width="5.798909667541557in"
height="4.090487751531058in"}

- What is the purpose of compression when creating an archive?

To reduce file size and save storage space.

- Which command is used to compress files into a gzip archive in Linux?

Use \'gzip filename\'.

![](images/media/image146.tmp){width="5.736406386701662in"
height="1.8612062554680664in"}

- How can you extract files from a gzip archive in Linux?

Use \'gunzip filename.gz\'.

![](images/media/image147.tmp){width="6.0in"
height="3.8965277777777776in"}

- How can you extract files from a bzip archive in Linux?

Use \'bunzip2 filename.bz2\'.

![](images/media/image148.tmp){width="3.8265857392825895in"
height="0.25001312335958004in"}

- What is the difference between a tar archive and a compressed archive?

Tar groups files; compression reduces size.

- How can you create a zip archive of files and directories in Linux?

Use \'zip -r archive.zip files\'.

![](images/media/image149.tmp){width="5.722516404199475in"
height="4.041874453193351in"}

![](images/media/image150.tmp){width="5.500282152230971in"
height="1.0833891076115485in"}

- What command is used to extract files from a zip archive in Linux?

Use \'unzip archive.zip\'.

![](images/media/image151.tmp){width="3.6390758967629044in"
height="0.47919181977252845in"}

- How can you transfer files between Linux systems using the scp
  command?

Use \'scp file user@remote:/path\'.

- What is the syntax for transferring a file using scp?

scp source_file user@host:/destination

- How can you transfer an entire directory using scp?

Use \'scp -r directory user@host:/destination\'.

## 14. RPM Packages in Linux

- What is an RPM package in Linux?

A software package format used in Red Hat-based systems.

- How can you install an RPM package in Linux?

Use \'rpm -ivh package.rpm\'.

![](images/media/image152.tmp){width="5.778075240594926in"
height="1.1945056867891513in"}

![](images/media/image153.tmp){width="6.0in"
height="0.8986111111111111in"}

- What command is used to query information about an installed RPM
  package?

Use \'rpm -qi package_name\'.

![](images/media/image154.tmp){width="6.0in"
height="2.495138888888889in"}

- How can you list all the files installed by an RPM package?

Use \'rpm -ql package_name\'.

![](images/media/image155.tmp){width="6.0in"
height="1.2034722222222223in"}

- What is the purpose of the RPM database in Linux?

It stores information about installed packages.

- What command is used to upgrade an installed RPM package to a newer
  version?

Use \'rpm -Uvh package.rpm\'.

![](images/media/image156.tmp){width="6.0in"
height="0.7583333333333333in"}

- How can you remove an installed RPM package from the system?

Use \'rpm -e package_name\'.

![](images/media/image157.tmp){width="4.798858267716535in"
height="0.2847364391951006in"}

- What is the purpose of dependency resolution in RPM packages?

It ensures all required packages are installed.

- How can you list the dependencies of an RPM package?

Use \'rpm -qpR package.rpm\'.

![](images/media/image158.tmp){width="6.0in"
height="1.8555555555555556in"}

## 15. Yum in Linux

- What is Yum and what is its purpose in Linux?

Yum is a package manager for managing RPM packages with dependency
resolution.

- How can you install a package using Yum in Linux?

Use \'yum install package_name\'.

![](images/media/image159.tmp){width="6.0in"
height="0.8881944444444444in"}

- What command is used to search for packages using Yum?

Use \'yum search keyword\'.

![](images/media/image160.tmp){width="6.0in"
height="0.9423611111111111in"}

- How can you update all installed packages using Yum?

Use \'yum update\'.

![](images/media/image161.tmp){width="6.0in"
height="2.4722222222222223in"}

![](images/media/image162.tmp){width="6.0in"
height="0.5958333333333333in"}

- What is the purpose of repositories in Yum?

They provide sources for software installation and updates.

- How can you enable or disable a repository in Yum?

Edit .repo files or use \'yum-config-manager\'.

- What command is used to list the enabled repositories in Yum?

Use \'yum repolist enabled\'.

![](images/media/image163.tmp){width="6.0in"
height="0.9159722222222222in"}

- How can you install a specific version of a package using Yum?

Use \'yum install package-name-version\'.

![](images/media/image164.tmp){width="6.0in"
height="1.0888888888888888in"}

- What is the difference between Yum and RPM?

Yum resolves dependencies automatically; RPM does not.

- How can you list the dependencies of a package using Yum?

Use \'yum deplist package_name\'.

![](images/media/image165.tmp){width="6.0in" height="3.88125in"}

- How can you install a package group using Yum?

Use \'yum groupinstall \"Group Name\"\'.

## Yum Repositories in Linux

- What is a Yum repository in Linux?

A storage location that contains RPM packages for Yum.

- How can you configure a custom Yum repository in Linux?

Create a .repo file under /etc/yum.repos.d/.

![](images/media/image166.tmp){width="4.062708880139983in"
height="0.8333759842519685in"}

- What is the purpose of the baseurl directive in a Yum repository
  configuration?

It defines the path or URL to the repository source.

- How can you remove a Yum repository from the system?

Delete its .repo file from /etc/yum.repos.d/.

![](images/media/image167.tmp){width="4.778023840769904in"
height="0.4305774278215223in"}

![](images/media/image168.tmp){width="6.0in"
height="2.6840277777777777in"}

- What is the role of the yum.repos.d directory in Yum repositories?

It stores all Yum repository configuration files.

- What command is used to synchronize the metadata of a Yum repository?

Use \'yum makecache\'.

- What are some common Yum repository management commands in Linux?

yum repolist, yum clean all, yum makecache.

## 16. SSH in Linux

- What is SSH?

SSH (Secure Shell) is a protocol for securely accessing remote systems.

- Port number of SSH?

Default SSH port is 22.

- Is it possible to change SSH port number?

Yes, by editing /etc/ssh/sshd_config.

![](images/media/image169.tmp){width="5.007201443569554in"
height="0.26390201224846893in"}

![](images/media/image170.tmp){width="6.0in"
height="3.8819444444444446in"}

- Write command to login remote machine in terminal?

ssh user@hostname

- Write command to login local machine in terminal?

ssh localhost

- SSH configuration file location?

/etc/ssh/sshd_config

- Configure SSH key based authentication? write path of key file
  location? server1-user:admin1 to server2-user:admin1

Generate key with ssh-keygen, copy to \~/.ssh/authorized_keys on remote
server.

- What is the command to generate the SSH key?

ssh-keygen

- What is the command to copy the keys to remote machine?

ssh-copy-id user@remote_host

- When you generate the key what are files will be created?

id_rsa (private) and id_rsa.pub (public).

- What is the SSH daemon name?

sshd

- Write SSH service-related commands which you know?

systemctl start\|stop\|restart\|status sshd

- Disable SSH root login?

Edit /etc/ssh/sshd_config and set \'PermitRootLogin no\'.

- How to disable password-based authentication?

Set \'PasswordAuthentication no\' in sshd_config.

- Allow SSH access to particular user? (user1, user2, user3)

Add \'AllowUsers user1 user2 user3\' in sshd_config.

- Change SSH port number 4044 and try to SSH login.

Edit sshd_config Port 4044 and restart sshd.

- How to start, stop, restart, check the status of SSH service?

systemctl start\|stop\|restart\|status sshd

- How to start the SSH service permanently?

Enable at boot using \'systemctl enable sshd\'.

- How to stop the SSH service permanently?

Disable it using \'systemctl disable sshd\'.

## 17. Analyzing and Storing Logs in Linux

- What is the purpose of log files in Linux?

Log files record system, application, and user activity, helping
administrators monitor and troubleshoot issues.

- How can you view the contents of a log file in Linux?

You can use commands like \`cat\`, \`less\`, \`more\`, or \`tail\` to
view log contents. Example: \`less /var/log/messages\`.

![](images/media/image171.tmp){width="6.0in"
height="1.4631944444444445in"}

- What command is used to search for specific keywords or patterns
  within a log file?

Use the \`grep\` command. Example: \`grep error /var/log/messages\`.

![](images/media/image172.tmp){width="6.0in"
height="1.0326388888888889in"}

- How can you filter log entries based on specific criteria using the
  grep command?

You can combine \`grep\` with options like \`-i\` for case-insensitive
search or \`-E\` for regular expressions. Example: \`grep -i failed
/var/log/secure\`.

![](images/media/image173.tmp){width="6.0in"
height="0.5631944444444444in"}

- What is the purpose of log rotation in Linux?

Log rotation prevents log files from growing indefinitely by compressing
and archiving old logs automatically.

- How can you configure log rotation for a specific log file?

Edit or create configuration files in \`/etc/logrotate.d/\` and define
rotation rules for that log file.

- What is the significance of log levels in log files?

Log levels (e.g., info, warning, error, critical) indicate the severity
of events to help prioritize troubleshooting.

- How can you analyze logs for errors and warnings using regular
  expressions?

Use \`grep -E \'error\|warning\' /var/log/messages\` to find matching
entries.

![](images/media/image174.tmp){width="6.0in"
height="1.8270833333333334in"}

- What are some commonly used log files in Linux?

/var/log/messages, /var/log/secure, /var/log/cron, /var/log/dmesg,
/var/log/httpd/.

- How can you monitor log files in real-time using the tail command?

Use \`tail -f /var/log/messages\` to continuously watch new log entries.

![](images/media/image175.tmp){width="6.0in"
height="1.457638888888889in"}

- What is the purpose of log analyzers and monitoring tools in Linux?

Tools like \`journalctl\`, \`logwatch\`, help visualize, filter, and
analyze logs efficiently.

![](images/media/image176.tmp){width="6.0in"
height="2.423611111111111in"}

- How can you store logs remotely using a centralized logging server?

By configuring \`rsyslog\` or \`syslog-ng\` to send logs to a remote log
server using TCP/UDP.

- What is the role of the /var/log directory in Linux?

It stores all system and service log files used for auditing and
troubleshooting.

## 18. Access Control Lists (ACL)

- Set a read and write ACL for user bob on the file
  /home/user1/report.txt.

Command: \`setfacl -m u:bob:rw /home/user1/report.txt\`.

![](images/media/image177.tmp){width="4.923863735783027in"
height="3.6321314523184602in"}

- Remove all ACL entries for the file /var/log/syslog.

Command: \`setfacl -b /var/log/syslog\`.

![](images/media/image178.tmp){width="3.3265594925634296in"
height="3.6876891951006123in"}

- Grant the group developers read, write, and execute permissions on the
  directory /home/projects/, including all files and subdirectories.

Command: \`setfacl -R -m g:developers:rwx /home/projects/\`.

![](images/media/image179.tmp){width="5.528062117235345in"
height="2.465404636920385in"}

- Set a default ACL that gives the group marketing read-only access to
  all new files created in the directory /shared/marketing/.

Command: \`setfacl -d -m g:marketing:r /shared/marketing/\`.

![](images/media/image180.tmp){width="6.0in"
height="3.082638888888889in"}

- Check and display all the ACL entries on the file /etc/hosts.

Command: \`getfacl /etc/hosts\`.

![](images/media/image181.tmp){width="5.326662292213474in"
height="2.062606080489939in"}

- Set the user alice to have no permissions on the file
  /home/user2/confidential.txt, even though she belongs to the users
  group which has permissions.

Command: \`setfacl -m u:alice:\-\-- /home/user2/confidential.txt\`.

![](images/media/image182.tmp){width="6.0in"
height="2.404861111111111in"}

- Grant the user tom execute permission on the directory /scripts/ and
  all files inside it.

Command: \`setfacl -R -m u:tom:x /scripts/\`.

![](images/media/image183.tmp){width="5.4169455380577425in"
height="3.1876640419947506in"}

- Modify the ACL of the file /data/project.txt to grant the user susan
  read and write permissions, but not execute permissions.

Command: \`setfacl -m u:susan:rw /data/project.txt\`.

![](images/media/image184.tmp){width="5.486393263342082in"
height="2.645968941382327in"}

- Set an ACL for the group admin to have full permissions (read, write,
  execute) on the file /etc/passwd, while keeping the original
  permissions for other users intact.

Command: \`setfacl -m g:admin:rwx /etc/passwd\`.

![](images/media/image185.tmp){width="5.361386701662292in"
height="2.88209208223972in"}

- Create an ACL that removes write permissions for the group staff on
  the file /tmp/notes.txt, but allows the owner to retain full
  permissions.

Command: \`setfacl -m g:staff:r-x /tmp/notes.txt\`.

![](images/media/image186.tmp){width="5.46555883639545in"
height="2.4584601924759406in"}

## Network Configuration

- Add additional ethernet card and assign static ip

Use \`nmcli\` or edit network scripts. Example:\
\`nmcli con add type ethernet ifname eth1 ip4 192.168.1.10/24 gw4
192.168.1.1\`.

![](images/media/image187.tmp){width="6.0in"
height="4.045138888888889in"}

- Add additional ethernet card and assign dynamic ip

Use DHCP: \`nmcli con add type ethernet ifname eth1\`.

![](images/media/image188.tmp){width="6.0in"
height="0.32569444444444445in"}

- How to check the server IP also show the current IP details?

Use \`ip addr show\` or \`ifconfig\`.

![](images/media/image189.tmp){width="6.0in"
height="2.9451388888888888in"}

- How to check the server routes also show current route details?

Use \`ip route show\` or \`route -n\`.

![](images/media/image190.tmp){width="6.0in" height="1.03125in"}

- Add two ethernet card and assign one ip?

Configure bonding or teaming using
\`/etc/sysconfig/network-scripts/ifcfg-bond0\`.

- Assign two ip address for one Ethernet card?

Use \`ip addr add 192.168.1.11/24 dev eth0\` for the second IP.

- How to check the server hostname

Use \`hostname\` or \`hostnamectl\`.

- Change server hostname as server.glotechcorp.com permanently

Use \`hostnamectl set-hostname server.glotechcorp.com\` and update
\`/etc/hostname\`.
