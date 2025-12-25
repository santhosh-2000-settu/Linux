#  Find and locate

The \'find\' command in Linux is used to search for files and
directories based on various criteria such as name, type, permissions,
size, owner, and timestamps. Below is a comprehensive list of commonly
used \'find\' command examples and options.

## Locate Command

locate \<dir name\>\
locate \<file name\>

![A screen shot of a computer](images/media/image1.tmp){width="6.0in"
height="2.0590277777777777in"}

The \'locate\' command is used to find files and directories quickly
using a pre-built database. It is much faster than \'find\' but may not
show very recent changes unless the database is updated using
\'updatedb\'.

## Common \'find\' Command Examples

- Find Files Using Name in Current Directory:

find . -name data.txt

![](images/media/image2.tmp){width="3.9586767279090114in"
height="0.6167202537182852in"}

- Find Files Under Home Directory:

find /home -name test.txt

![](images/media/image3.tmp){width="5.283791557305337in"
height="0.5667158792650918in"}

- Find Files Using Name and Ignoring Case:

find /home -iname data.txt

![A screen shot of a computer AI-generated content may be
incorrect.](images/media/image4.tmp){width="4.5920647419072615in"
height="3.308619860017498in"}

- Find Directories Using Name:

find / -type d -name Data

![A black background with white text AI-generated content may be
incorrect.](images/media/image5.tmp){width="4.708741251093613in"
height="0.6333880139982502in"}

- Find PHP Files Using Name:

find . -type f -name index.php

![](images/media/image6.tmp){width="4.975430883639545in"
height="0.4500393700787402in"}

- Find all PHP Files in the Directory:

find . -type f -name \"\*.php\"

![A black background with white text AI-generated content may be
incorrect.](images/media/image7.tmp){width="4.88375656167979in"
height="0.7917355643044619in"}

- Find Files With 777 Permissions:

find . -type f -perm 0777 -print

![A screenshot of a computer AI-generated content may be
incorrect.](images/media/image8.tmp){width="6.0in"
height="3.439583333333333in"}

- Find Files Without 777 Permissions:

find / -type f ! -perm 777

![](images/media/image9.tmp){width="4.825417760279965in"
height="0.2000174978127734in"}

![A screenshot of a computer program AI-generated content may be
incorrect.](images/media/image10.tmp){width="4.43371719160105in"
height="7.267296587926509in"}

- Find SGID Files with 644 Permissions:

find / -perm 2644

![A computer screen with white text AI-generated content may be
incorrect.](images/media/image11.tmp){width="6.0in"
height="1.0284722222222222in"}

- Find Sticky Bit Files with 551 Permissions:

find / -perm 1551

![A black screen with white text AI-generated content may be
incorrect.](images/media/image12.tmp){width="6.0in"
height="0.9541666666666667in"}

- Find SUID Files:

find / -perm /u=s

![A screenshot of a computer AI-generated content may be
incorrect.](images/media/image13.tmp){width="6.0in"
height="5.417361111111111in"}

- Find SGID Files:

find / -perm /g=s

![A screenshot of a computer AI-generated content may be
incorrect.](images/media/image14.tmp){width="6.0in"
height="2.984722222222222in"}

- Find Read-Only Files:

find / -perm /u=r

![A computer screen with white text AI-generated content may be
incorrect.](images/media/image15.tmp){width="6.0in" height="1.5in"}

- Find Executable Files:

find / -perm /a=x

![A screenshot of a computer AI-generated content may be
incorrect.](images/media/image16.tmp){width="6.0in"
height="5.902777777777778in"}

- Find Files with 777 Permissions and Chmod to 644:

find / -type f -perm 0777 -print -exec chmod 644 {} \\;

![](images/media/image17.tmp){width="6.0in" height="0.7in"}

- Find Directories with 777 Permissions and Chmod to 755:

find / -type d -perm 777 -print -exec chmod 755 {} \\;

![](images/media/image18.tmp){width="6.0in"
height="0.35347222222222224in"}

- Find and remove single File:

find . -type f -name \"tecmint.txt\" -exec rm -f {} \\;

![](images/media/image19.tmp){width="6.0in"
height="0.38333333333333336in"}

- Find and remove Multiple Files:

find . -type f -name \"\*.txt\" -exec rm -f {} \\;

![](images/media/image20.tmp){width="6.0in"
height="0.36944444444444446in"}

- Find all Empty Files:

find / -type f -empty

![A computer screen shot of white text AI-generated content may be
incorrect.](images/media/image21.tmp){width="6.0in"
height="1.7131944444444445in"}

- Find all Empty Directories:

find /tmp -type d -empty

![A computer screen shot of a black screen AI-generated content may be
incorrect.](images/media/image22.tmp){width="4.567062554680665in"
height="3.0752668416447944in"}

- Find all Hidden Files:

find /tmp -type f -name \".\*\"

![A screen shot of a computer AI-generated content may be
incorrect.](images/media/image23.tmp){width="4.692073490813648in"
height="1.600138888888889in"}

- Find Single File Based on User:

find / -user root -name tecmint.txt

![A black screen with white text AI-generated content may be
incorrect.](images/media/image24.tmp){width="4.700406824146982in"
height="0.9834186351706037in"}

- Find all Files Based on User:

find /home -user tecmint

![A screen shot of a computer AI-generated content may be
incorrect.](images/media/image25.tmp){width="6.0in"
height="3.1486111111111112in"}

- Find all Files Based on Group:

find /home -group developer

![A computer screen shot of a black screen AI-generated content may be
incorrect.](images/media/image26.tmp){width="4.3587106299212595in"
height="2.5668886701662292in"}

- Find Particular Files of User:

find /home -user tecmint -iname \"\*.txt\"

![](images/media/image27.tmp){width="6.0in"
height="0.5819444444444445in"}

- Find Last 50 Days Modified Files:

find / -mtime 50

![A screen shot of a computer AI-generated content may be
incorrect.](images/media/image28.tmp){width="3.65031605424322in"
height="7.492316272965879in"}

- Find Last 50 Days Accessed Files:

find / -atime 50

![A screenshot of a computer program AI-generated content may be
incorrect.](images/media/image29.tmp){width="3.600311679790026in"
height="7.867347987751531in"}

- Find Last 50-100 Days Modified Files:

find / -mtime +50 -mtime -100

- Find Changed Files in Last 1 Hour:

find / -cmin -60

![A screen shot of a computer AI-generated content may be
incorrect.](images/media/image30.tmp){width="3.441965223097113in"
height="8.200710848643919in"}

- Find Modified Files in Last 1 Hour:

find / -mmin -60

![A screenshot of a computer AI-generated content may be
incorrect.](images/media/image31.tmp){width="3.65031605424322in"
height="6.00051946631671in"}

- Find Accessed Files in Last 1 Hour:

find / -amin -60

![A screen shot of a computer AI-generated content may be
incorrect.](images/media/image32.tmp){width="3.6253138670166227in"
height="5.392133639545057in"}

- Find 50MB Files:

find / -size 50M

![A black screen with white text AI-generated content may be
incorrect.](images/media/image33.tmp){width="6.0in"
height="0.8826388888888889in"}

- Find Size between 50MB -- 100MB:

find / -size +50M -size -100M

![](images/media/image34.tmp){width="4.850419947506562in"
height="7.64232939632546in"}

- Find and Delete 100MB Files:

find / -type f -size +100M -exec rm -f {} \\;

- Find Specific Files and Delete:

find / -type f -name \*.mp3 -size +10M -exec rm {} \\;

![](images/media/image35.tmp){width="6.0in"
height="0.36041666666666666in"}

## Explanation of Key Options

- -type: Specifies the type of item to find (f = file, d = directory, l
  = symlink).

- -size: Searches files based on size (e.g., +100M for greater than
  100MB).

- -user: Finds files owned by a specific user.

- -group: Finds files belonging to a specific group.

- -perm: Searches files with specific permission bits (e.g., 777, 644).

- -delete: Deletes matching files or directories (use with caution).

- -exec: Executes a command on each matching file (e.g., rm, chmod,
  chown).

- -print: Displays the path of each matching file or directory.

- -mtime: Finds files modified N days ago.

- -mmin: Finds files modified N minutes ago.

- -atime: Finds files last accessed N days ago.

- -amin: Finds files last accessed N minutes ago.

- -cmin: Finds files whose status (metadata) changed within N minutes.
