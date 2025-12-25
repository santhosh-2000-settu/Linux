#  Disk Management

Disk Management in Linux involves handling storage devices, creating
partitions, formatting file systems,\
and mounting them for use by the operating system. This guide explains
the essential concepts and commands\
used in Linux for managing disks and partitions.

What is file system?\
\
File System is a method to store and organize files and directories on
disk.\
A file system can have different formats called file system types.\
These formats determine how the information is stored as files and
directories.\
\
Hard disk & pendrive\
\
Windows file system\
\
FAT\
FAT32\
NTFS

## Linux File Systems

A file system defines how data is stored and retrieved on a storage
device. Linux supports multiple file systems,\
each offering different features and performance characteristics.

•ext1\
• ext2\
• ext3\
• ext4 -- Default file system in RHEL/OEL-6\
• XFS -- Default file system in RHEL/OEL-7/8/9\
• Swap (used for virtual memory)

Ext2\
1. Ext2 stands for second extended file system.\
2. Ext2 does not have journaling feature.\
3. Maximum individual file size can be from 16 GB to 2 TB\
4. Overall ext2 file system size can be from 2 TB to 32 TB\
\
Ext3\
1. Ext3 stands for third extended file system.\
2. Starting from Linux Kernel 2.4.15 ext3 was available.\
3. The main benefit of ext3 is that it allows journaling.\
4. Journaling has a dedicated area in the file system, where all the
changes are tracked.\
When the system crashes, the possibility of file system corruption is
less because of journaling.\
5. Maximum individual file size can be from 16 GB to 2 TB\
6. Overall ext3 file system size can be from 2 TB to 32 TB\
7. There are three types of journaling available in ext3 file system.\
- Journal -- Metadata and content are saved in the journal.\
- Ordered -- Only metadata is saved in the journal (default).\
- Writeback -- Only metadata is saved in the journal (order not
guaranteed).\
8. You can convert an ext2 file system to ext3 file system directly
(without backup/restore).\
\
Ext4\
\
1. Ext4 stands for fourth extended file system.\
2. It was introduced in 2008.\
3. Starting from Linux Kernel 2.6.19 ext4 was available.\
4. Supports huge individual file size and overall file system size.\
5. Maximum individual file size can be from 16 GB to 16 TB\
6. Overall maximum ext4 file system size is 1 EB (exabyte).\
7. Directory can contain a maximum of 64,000 subdirectories (vs 32,000
in ext3).\
\
XFS File System\
\
1. The XFS file system is a high-performance 64-bit journaling file
system.\
2. The support of XFS was merged into Linux kernel around 2002.\
3. Red Hat Enterprise Linux version 5.4 started using XFS in 2009.\
4. XFS supports maximum file system size of 8 exbibytes.\
5. Drawbacks: cannot shrink and has poor performance when deleting large
numbers of files.\
6. RHEL 7+ uses XFS as the default filesystem.

- Command to check the kernel version:

  \# uname -r

  ![](images/media/image1.tmp){width="2.368176946631671in"
  height="0.4444674103237095in"}

## Partition Tables

Partition tables define how disk space is divided into partitions. There
are two main types of partition tables in Linux:

• MBR (Master Boot Record)

• GPT (GUID Partition Table)

### MBR (Master Boot Record)

The MBR partitioning scheme allows a maximum of four partitions:\
• 3 primary partitions\
• 1 extended partition (which can contain multiple logical partitions)

### GPT (GUID Partition Table)

The GPT partitioning scheme allows up to 128 partitions and supports
larger disk sizes.

Used to list information about all available block devices in Linux.\
\
Examples:\
\# lsblk

![](images/media/image2.tmp){width="5.305827865266842in"
height="1.5764698162729658in"}

\# lsblk /dev/sdb\
\# lsblk -o name,size\
\
Device naming:\
IDE \--\> /dev/hda\
SCSI/SATA \--\> /dev/sda\
AWS (Xen) \--\> /dev/xvda\
NVMe \--\> /dev/nvme0n1

## Disk Scanning and Partitioning

To detect new disks or scan for new storage devices, use the following
command:

\# echo \'- - -\' \> /sys/class/scsi_host/host\<N\>/scan

You typically need to scan three hosts: host0, host1, and host2.

![](images/media/image3.tmp){width="5.562785433070866in"
height="0.2083442694663167in"}

### MBR (Master Boot Record)

To create a partition (for MBR/DOS):

\# fdisk -l /dev/sdb -- Lists the existing partitions

![](images/media/image4.tmp){width="4.875250437445319in"
height="1.1042235345581801in"}

\# fdisk /dev/sdb -- Opens the partitioning utility

![](images/media/image5.tmp){width="5.722516404199475in"
height="1.777869641294838in"}

![](images/media/image6.tmp){width="4.743299431321085in"
height="4.903029308836396in"}

![](images/media/image7.tmp){width="5.034981408573929in"
height="2.215391513560805in"}

Inside the fdisk utility, you can use the following commands:

• p -- Print the partition table\
• n -- Create a new partition\
• p -- Create a primary partition\
• e -- Create an extended partition\
• l -- Create a logical partition (inside an extended partition)\
• Specify partition number (e.g., 1, 2, 3\...)\
• Specify last sector or size (e.g., +2G to create a 2 GB partition)

![](images/media/image8.tmp){width="6.0in" height="4.252777777777778in"}

![](images/media/image9.tmp){width="6.0in"
height="0.9576388888888889in"}

![](images/media/image10.tmp){width="5.430834426946632in"
height="2.138999343832021in"}

To check disk usage:

\# df -hT

![](images/media/image11.tmp){width="6.0in"
height="1.4826388888888888in"}

## File System Creation and Mounting

Once partitions are created, they must be formatted with a file system
before use.

Examples:

\# mkfs.xfs /dev/sdb1

![](images/media/image12.tmp){width="6.0in"
height="1.823611111111111in"}

\# mkfs -t xfs /dev/sdb2 (use -t to specify the file system type)

To mount the file system:

\# mkdir /data (create mount point directory)

![](images/media/image13.tmp){width="2.583465660542432in"
height="0.576418416447944in"}

\# mount /dev/sdb1 /data (mounts the device)

![](images/media/image14.tmp){width="3.5349037620297463in"
height="0.5000251531058618in"}

To verify and use:

cd /data\
mkdir dir\
ls

![](images/media/image15.tmp){width="4.298832020997375in"
height="1.2847878390201224in"}

To unmount the file system:

\# umount /data

![](images/media/image16.tmp){width="2.729306649168854in"
height="0.7569838145231846in"}

Temporary mounts are stored in /etc/mtab.\
To check recent mounts:\
\# tail /etc/mtab

![](images/media/image17.tmp){width="6.0in"
height="1.1666666666666667in"}

If the system reboots, temporary mounts will be lost.

To check UUID number

#lsblk -f

![](images/media/image18.tmp){width="6.0in"
height="1.2465277777777777in"}

###  GPT (GUID Partition Table)

To create a partition for gpt

![](images/media/image19.tmp){width="5.014146981627297in"
height="2.15288823272091in"}

![](images/media/image20.tmp){width="5.618344269466316in"
height="0.9514381014873141in"}

![](images/media/image21.tmp){width="4.069653324584427in"
height="4.833581583552056in"}

Once partitions are created, they must be formatted with a file system
before use.

Examples:

\# mkfs.xfs /dev/sdb1

![](images/media/image22.tmp){width="6.0in" height="4.78125in"}

To mount the file system:

\# mkdir /data (create mount point directory)

![](images/media/image23.tmp){width="2.3820669291338583in"
height="0.4375229658792651in"}

\# mount /dev/sdb1 /data (mounts the device)

![](images/media/image24.tmp){width="3.7224136045494314in"
height="0.22917869641294839in"}

![](images/media/image25.tmp){width="6.0in"
height="1.6847222222222222in"}

To unmount the file system:

\# umount /data2

![](images/media/image26.tmp){width="6.0in"
height="1.6597222222222223in"}

## Making Mounts Permanent with /etc/fstab

To make mounts permanent across reboots, entries must be added to the
/etc/fstab file.

Edit the fstab file using:

\# vi /etc/fstab

Example /etc/fstab entry format:\
\| Device \| Mount Point \| File System Type \| Options \| Backup \|
Check Order \|\
\| :\-\-- \| :\-\-- \| :\-\-- \| :\-\-- \| :\-\-- \| :\-\-- \|\
\| /dev/sdb1 \| /data \| xfs \| defaults \| 0 \| 0 \|

![](images/media/image27.tmp){width="2.6181900699912513in"
height="0.2777919947506562in"}

![](images/media/image28.tmp){width="6.0in"
height="2.698611111111111in"}

Field explanations:\
• Device -- The block device name (e.g., /dev/sdb1).\
• Mount Point -- Directory where the device is mounted.\
• File System Type -- Type of file system (e.g., xfs, ext4).\
• Options -- Mount options (e.g., defaults, rw, noatime).\
• Backup -- \'1\' if dump utility should back up the partition, \'0\'
otherwise.\
• Check Order -- Determines the order fsck checks file systems at boot.
Root is usually 1, others 2.

To activate all entries in /etc/fstab:\
\# mount -a

![](images/media/image29.tmp){width="6.0in"
height="1.711111111111111in"}\
\
To unmount a permanent mount:\
• Remove or comment out the entry from /etc/fstab

![](images/media/image30.tmp){width="6.0in"
height="2.0416666666666665in"}

• Run \# umount /data

![](images/media/image31.tmp){width="2.7570866141732284in"
height="0.2708475503062117in"}

• Reboot after removing the hard disk or fstab entry.

![](images/media/image32.tmp){width="6.0in"
height="1.6791666666666667in"}
