Auto FS

**AUTOFS:**

- Automount uses the service to automatically mount filesystems when
  they are accessed and unmount them after a period of inactivity .

In Server Side:

**Ensure NFS server is set up and a share is available**

#vi /etc/exports

![](media/image1.tmp){width="4.840526027996501in"
height="1.4514632545931758in"}

**In the client side:**

**Install autofs package:**

#yum install autofs

![](media/image2.tmp){width="5.768055555555556in"
height="3.6458333333333335in"}

**Create directory:**

#mkdir samplenfs

![](media/image3.tmp){width="2.868203193350831in"
height="0.22917869641294839in"}

**Edit the config file and add:**

**\#**vi /etc/auto.master

![](media/image4.tmp){width="3.1112707786526683in"
height="0.25001312335958004in"}

![](media/image5.tmp){width="5.768055555555556in"
height="4.6409722222222225in"}

**Create /etc/auto.misc**

#vi /etc/auto.misc

![](media/image6.tmp){width="5.701681977252844in"
height="3.229332895888014in"}

**Restart autofs:**

#sudo systemctl restart autofs

![](media/image7.tmp){width="4.2502187226596675in"
height="0.4305774278215223in"}

#cd content

**To check the shared dir has mounted in the client's dir:**

#df --Th:

![](media/image8.tmp){width="5.768055555555556in"
height="1.5888888888888888in"}

**Access the directory to see if it auto mounts:**

#cd /content/

#ls

![](media/image9.tmp){width="3.180718503937008in"
height="0.9722725284339457in"}
