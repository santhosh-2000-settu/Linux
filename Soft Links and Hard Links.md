# Soft Links and Hard Links in Linux

In Linux, links are references to files. There are two main types of
links: Soft Links (Symbolic Links) and Hard Links. Both serve the
purpose of creating references, but they work differently at the
filesystem level.

## 1. Soft Links (Symbolic Links)

• A soft link is more like a shortcut to the original file.\
• It contains the pathname of the target file, rather than pointing
directly to the inode.\
• Soft links have their own inode and are independent files.\
• If the original file is deleted, the soft link becomes a \'broken
link\'.\
• Soft links can span across different filesystems or partitions.\
• Can be created for both files and directories.

• To create a soft link:\
ln -s original_file softlink_name

![](images/media/image1.png){width="5.767361111111111in"
height="2.066666666666667in"}

## 2. Hard Links

• A hard link is essentially another name for an existing file.\
• It points directly to the inode of the file, meaning both the original
file and the hard link share the same inode number.\
• Changes made to one file are reflected in the other, since they
reference the same inode.\
• Deleting the original file does not remove the data as long as a hard
link exists.\
• Hard links cannot span across different filesystems or partitions.\
• Cannot be created for directories (to prevent loops).

• To create a hard link:\
ln original_file hardlink_name

![](images/media/image2.png){width="5.768055555555556in"
height="2.2243055555555555in"}

## 3. Key Differences

Hard Links:\
- Share the same inode number as the original file.\
- Cannot span across filesystems.\
- Remain valid even if the original file is deleted.\
- Cannot link directories.\
\
Soft Links:\
- Have a different inode number than the target file.\
- Can span across filesystems.\
- Become invalid if the target file is deleted.\
- Can link directories.
