#  Swap 

Swap is a space on a disk that is used when the amount of physical RAM
memory is full. When a Linux system runs out of RAM, inactive pages are
moved from the RAM to the swap space. Swap space can take the form of
either a dedicated swap partition or a swap file.

## Checking Swap

To check swap usage:

- \# free -m\
  \# free -g

  ![](images/media/image1.png){width="5.99375in"
  height="1.8430555555555554in"}

## Creating Swap Space

Swap can be created in two ways:

(i) Disk Partition,

(ii) File

To check available space:

\# df -h

![](images/media/image2.png){width="5.9944444444444445in"
height="2.673611111111111in"}

Steps to create a swap file:

1.  Create file with specific size:

    \# fallocate -l 1G /swapfile

    ![](images/media/image3.png){width="5.008333333333334in"
    height="0.35in"}

    ![](images/media/image4.png){width="5.995138888888889in"
    height="4.565277777777778in"}

2.  Set permissions so only root can access:

    \# chmod 600 /swapfile

    ![](images/media/image5.png){width="5.998611111111111in"
    height="4.164583333333334in"}

3.  Make file a swap area:

    \# mkswap /swapfile

    ![](images/media/image6.png){width="5.993055555555555in"
    height="0.6222222222222222in"}

4.  Enable swap:

    \# swapon /swapfile

    ![](images/media/image7.png){width="3.8916666666666666in"
    height="0.325in"}

5.  Verify: \# free -m

    ![](images/media/image8.png){width="5.997916666666667in"
    height="0.8069444444444445in"}

    It will only hold on till you reboot

To make permanent changes,

#vi /etc/fstab and add an entry like:

swapfile swap swap defaults 0 0

![](images/media/image9.png){width="3.9916666666666667in"
height="0.3in"}

![](images/media/image10.png){width="5.989583333333333in"
height="3.5236111111111112in"}

![](images/media/image11.png){width="5.992361111111111in"
height="0.6645833333333333in"}

# Explanation of /etc/fstab Swap Entry

The following explains the meaning of each field in the /etc/fstab entry
for a swap file:

/swapfile01 swap swap defaults 0 0

+-----------------------+-----------------------+-----------------------+
| Field                 | Example               | Meaning               |
+-----------------------+-----------------------+-----------------------+
| 1\. Device            | /swapfile01           | The path to the swap  |
|                       |                       | file (or device).     |
|                       |                       | Here it's a file      |
|                       |                       | called /swapfile01.   |
+-----------------------+-----------------------+-----------------------+
| 2\. Mount Point       | swap                  | Indicates that this   |
|                       |                       | entry is a swap area, |
|                       |                       | not a normal          |
|                       |                       | directory mount.      |
+-----------------------+-----------------------+-----------------------+
| 3\. Filesystem Type   | swap                  | Specifies the type of |
|                       |                       | filesystem. For swap  |
|                       |                       | space, this is always |
|                       |                       | swap.                 |
+-----------------------+-----------------------+-----------------------+
| 4\. Options           | defaults              | Mount options. For    |
|                       |                       | swap, just defaults   |
|                       |                       | (use default          |
|                       |                       | behavior).            |
+-----------------------+-----------------------+-----------------------+
| 5\. Dump              | 0                     | Used by the dump      |
|                       |                       | backup utility.       |
|                       |                       |                       |
|                       |                       | 0 = do not back up.   |
|                       |                       |                       |
|                       |                       | 1= backup             |
+-----------------------+-----------------------+-----------------------+
| 6\. Pass              | 0                     | Used by fsck at boot  |
|                       |                       | to check filesystems. |
|                       |                       |                       |
|                       |                       | 0 = do not check.     |
|                       |                       |                       |
|                       |                       | 1 = check main file / |
|                       |                       |                       |
|                       |                       | 2 = check all files   |
|                       |                       | other than /          |
+-----------------------+-----------------------+-----------------------+

**Removing Swap**

Steps to remove swap:

1.  Delete swap entry from /etc/fstab

    ![](images/media/image12.png){width="3.783333333333333in"
    height="0.30833333333333335in"}

    ![](images/media/image13.png){width="5.9944444444444445in"
    height="2.682638888888889in"}

2.  Turn off swap: \# swapoff /swapfile

    ![](images/media/image14.png){width="4.0in"
    height="0.31666666666666665in"}

3.  Remove file: \# rm /swapfile

    ![](images/media/image15.png){width="5.990972222222222in"
    height="0.9486111111111111in"}

## Swappiness Value

Swappiness is a Linux kernel property that defines how often the system
will use the swap space. It can have a value between 0 and 100. A low
value makes the kernel avoid swapping, while a high value makes it use
swap more aggressively.

Default values:

\- CentOS 7: 30\
- CentOS 9: 60

Example:

Swappiness 10 → 90% RAM used before swapping\
Swappiness 90 → 10% RAM used before swapping

To check swappiness:

\# sysctl vm.swappiness

![](images/media/image16.png){width="4.875in"
height="0.5666666666666667in"}

\# cat /proc/sys/vm/swappiness

To change temporarily:

\# sysctl vm.swappiness=10

![](images/media/image17.png){width="5.175in"
height="0.5583333333333333in"}

## Red Hat Swap Memory Recommendation

Recommended swap size according to Red Hat:

- Up to 2GB RAM → 2 × RAM

- 2GB - 8GB RAM → Equal to RAM

- 8GB - 64GB RAM → 0.5 × RAM

- 64GB or more → 4GB of swap space
