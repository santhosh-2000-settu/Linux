## Overview

To fix kernel panic issues caused by missing or corrupted initramfs
files in CentOS 9, using Rescue Mode and dracut to regenerate the
missing kernel files.

## Step 1: Check /boot Directory and initramfs Files

• Boot process loads GRUB from /boot.

• GRUB loads the kernel (vmlinuz) and initramfs.

• If initramfs is missing or corrupted, system fails to boot.

• Navigate to /boot and list initramfs files.

• /boot modifications require root privileges.

![](images/media/image1.tmp){width="6.0in" height="2.652083333333333in"}

## Step 2: Remove Corrupted initramfs File

• Remove the corrupted or problematic initramfs file from /boot.

• This file will later be regenerated using rescue mode.

![](images/media/image2.tmp){width="6.0in" height="2.540277777777778in"}

## Step 3: Reboot and Remove 'autonist' Entry

• Reboot the system.

• Before rebooting, open VM settings → Hard Disk.

• Remove the entry labeled \'autonist\'.

• Save and reboot again.

## Step 4: Boot From CD-ROM

• While the system restarts, press ESC within 5 seconds.

• Open the boot menu.

![](images/media/image3.tmp){width="2.6251345144356955in"
height="1.729255249343832in"}

• Select \*\*CD-ROM Drive\*\* to boot from installation media.

## Step 5: Enter Rescue Mode

• On CentOS installation screen, select \'Troubleshooting\'.

![](images/media/image4.tmp){width="4.034930008748907in"
height="1.7709241032370953in"}

• Select \'Rescue a CentOS Stream system\'.

![](images/media/image5.tmp){width="4.36133530183727in"
height="2.715417760279965in"}

• System loads rescue environment.

![](images/media/image6.tmp){width="5.0974846894138235in"
height="2.9376509186351707in"}

• Press 1 to continue.

![](images/media/image7.tmp){width="4.75024387576553in"
height="2.1737226596675416in"}

• Enter the rescue shell.

## Step 6: Regenerate initramfs Using dracut

Run the following commands:

1\) chroot /mnt/sysroot

\- Changes root directory to installed system.

2\) dracut \--regenerate-all \--force

\- Rebuilds initramfs for all installed kernels.

\- Fixes missing/broken kernel initramfs images.

![](images/media/image8.tmp){width="4.375225284339457in"
height="1.6598075240594925in"}

## Step 7: Reboot and Verify

• Exit chroot and reboot system.

![A screen shot of a computer AI-generated content may be
incorrect.](images/media/image9.tmp){width="3.5083333333333333in"
height="1.55in"}

• After system boots normally, log in as root.

• Navigate to /boot and verify that the missing initramfs file is now
restored.

![](images/media/image10.tmp){width="6.0in"
height="2.4694444444444446in"}
