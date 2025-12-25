#  Disk management (LVM) 

## LVM Basics

LVM (Logical Volume Manager) provides a more flexible approach to
managing disk storage compared to traditional partitioning. It allows
dynamic resizing and management of storage components.\
\
Hierarchy:\
Hard disks → Partitions → Physical Volume (PV) → Volume Group (VG) →
Logical Volume (LV) → Filesystem → Mount point\
\
- xfs: Can only extend (cannot reduce).\
- ext4: Can extend and reduce.

## Creating Physical Volumes (PV) and Volume Groups (VG)

![](images/media/image1.tmp){width="6.0in"
height="1.7555555555555555in"}

1\. Convert a disk/partition into a Physical Volume:\
\# pvcreate /dev/sdb /dev/sdc

![](images/media/image2.tmp){width="4.340500874890639in"
height="0.5625284339457568in"}

2\. Create a Volume Group (VG):\
\# vgcreate vg1 /dev/sdb

![](images/media/image3.tmp){width="4.021040026246719in"
height="0.4027985564304462in"}\
\
3. Extend an existing Volume Group:\
\# vgextend vg1 /dev/sdc

4\. Display Commands:\
\# pvs → Show physical volumes\
\# pvscan → Scan for PVs\
\# pvdisplay → Detailed PV info

![](images/media/image4.tmp){width="5.78501968503937in"
height="5.229435695538058in"}

![](images/media/image5.tmp){width="5.340552274715661in"
height="2.645968941382327in"}

\# vgs → Show volume groups\
\# vgscan → Scan for VGs

![](images/media/image6.tmp){width="4.30577646544182in"
height="0.6528116797900263in"}

\# vgdisplay → Detailed VG info

![](images/media/image7.tmp){width="5.333607830271216in"
height="5.222490157480315in"}

![](images/media/image8.tmp){width="5.118319116360455in"
height="3.020988626421697in"}

## Creating Logical Volumes (LV)

1\. Create a Logical Volume:\
\# lvcreate -L +5G -n lv1 vg1\
\# lvcreate \--size 5G \--name lv2 vg1\
\# lvcreate -l +25G -n lv3 vg1

![](images/media/image9.tmp){width="4.034930008748907in"
height="0.4236329833770779in"}

2\. Display LV info:\
\# lvs

![](images/media/image10.tmp){width="6.0in"
height="0.8159722222222222in"}

## Creating Filesystems and Mounting

After creating an LV, format it with a filesystem and mount it.\
\
1. Create filesystem:\
\# mkfs.xfs /dev/vg1/lv1\
\# mkfs -t ext4 /dev/vg1/lv2

![](images/media/image11.tmp){width="5.361386701662292in"
height="1.951489501312336in"}

2\. Create mount points and mount:\
\# mkdir /lv1\
\# mkdir /lv2\
\# mount /dev/vg1/lv1 /lv1\
\# mount /dev/vg1/lv2 /lv2

![](images/media/image12.tmp){width="3.493234908136483in"
height="0.36807414698162727in"}

![](images/media/image13.tmp){width="6.0in"
height="1.9701388888888889in"}

## Extending and Reducing Logical Volumes

1\. Extend a Logical Volume:\
\# lvextend -L +2G /dev/vg1/lv2

![](images/media/image14.tmp){width="6.0in"
height="1.9881944444444444in"}

2\. Reduce a Logical Volume (only for ext4):\
a. Unmount first:\
\# umount /dev/vg1/lv1

![](images/media/image15.tmp){width="6.0in"
height="1.8756944444444446in"}

b\. Check filesystem errors:\
\# e2fsck -f /dev/vg1/lv1

![](images/media/image16.tmp){width="6.0in"
height="1.3854166666666667in"}

c\. Resize filesystem:\
\# resize2fs /dev/vg1/lv1

![](images/media/image17.tmp){width="5.361386701662292in"
height="0.7917071303587052in"}

d\. Reduce LV size:\
\# lvreduce -L -3G /dev/vg1/lv1

![](images/media/image18.tmp){width="6.0in"
height="0.7444444444444445in"}

3\. Resize filesystem after extension:\
\# resize2fs /dev/vg1/lv1 (ext4)

![](images/media/image19.tmp){width="6.0in"
height="1.4319444444444445in"}

\# xfs_growfs /dev/vg1/lv1 (xfs)

## Post-Reduction and Verification

After resizing or reducing:\
- Run filesystem check (optional for xfs, mandatory for ext4).\
\# e2fsck -f /dev/vg1/lv1

![](images/media/image20.tmp){width="6.0in"
height="1.3909722222222223in"}

\- Mount again:\
\# mount /dev/vg1/lv1

![](images/media/image21.tmp){width="6.0in"
height="3.0618055555555554in"}

\- Verify:\
\# lvs\
![](images/media/image22.tmp){width="6.0in"
height="0.8006944444444445in"}

## Removing LVM Components

To remove LVM components:\
1. Remove mount entries from /etc/fstab.

![](images/media/image23.tmp){width="6.0in"
height="2.077777777777778in"}

2\. Unmount:\
\# umount /lv1 /lv2

![](images/media/image24.tmp){width="2.4167913385826774in"
height="0.40974300087489063in"}

3\. Remove logical volumes:\
\# lvremove /dev/vg1/lv1

![](images/media/image25.tmp){width="5.868357392825897in"
height="0.5833628608923884in"}

4\. Remove volume group:\
\# vgremove vg1

![](images/media/image26.tmp){width="6.0in"
height="1.8618055555555555in"}

5\. Remove physical volume:\
\# pvremove /dev/sdb

![](images/media/image27.tmp){width="6.0in"
height="1.1256944444444446in"}

Useful command:\
\# lsblk → Display block devices and hierarchy

![](images/media/image28.tmp){width="6.0in"
height="1.6493055555555556in"}
