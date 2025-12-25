Yum and DNF are package managers for RHEL, CentOS, and Fedora systems.
They allow users and system administrators to easily install, update,
remove, and query software packages.

Yum and DNF are same

# Basic Commands

## Install a package

\# yum install \<package\>\
\# dnf install \<package\>

![](images/media/image1.png){width="5.990277777777778in"
height="1.0729166666666667in"}

## Install multiple packages

\# yum install \<pkg1\> \<pkg2\> ...

![](images/media/image2.png){width="5.999305555555556in"
height="2.089583333333333in"}

## Remove a package

\# yum remove \<package\>

\# dnf remove \<package\>

![](images/media/image3.png){width="5.988194444444445in"
height="1.73125in"}

## Install without confirmation

\# yum install \<package\> -y

![](images/media/image4.png){width="5.997222222222222in"
height="0.9798611111111111in"}

## List a package

\# yum list \<package\>

![](images/media/image5.png){width="5.992361111111111in"
height="0.5263888888888889in"}

## Update a package

\# yum update \<package\>

![](images/media/image6.png){width="5.989583333333333in"
height="0.7180555555555556in"}

## Search a package

\# yum search \<package\>

![](images/media/image7.png){width="5.991666666666666in"
height="2.4833333333333334in"}

![](images/media/image8.png){width="5.993055555555555in"
height="2.7819444444444446in"}

## View package info

\# yum info \<package\>

![](images/media/image9.png){width="5.993055555555555in"
height="3.046527777777778in"}

## View available packages

\# yum list\
(yum list \| less)

![](images/media/image10.png){width="5.990277777777778in"
height="2.6930555555555555in"}

## View installed packages

\# yum list installed

![](images/media/image11.png){width="5.991666666666666in"
height="2.68125in"}

## Find package providing a file

\# yum provides /usr/bin/mkdir

![](images/media/image12.png){width="5.997222222222222in"
height="3.109722222222222in"}

![](images/media/image13.png){width="5.995138888888889in"
height="4.148611111111111in"}

## Check updates

\# yum check-update

![](images/media/image14.png){width="5.999305555555556in"
height="2.8229166666666665in"}

## Update all packages

\# yum update

![](images/media/image15.png){width="5.998611111111111in"
height="2.5381944444444446in"}

![](images/media/image16.png){width="5.995833333333334in"
height="1.05625in"}

## View repositories

\# yum repolist

![](images/media/image17.png){width="5.996527777777778in"
height="3.032638888888889in"}

\# yum repolist all

![](images/media/image18.png){width="5.990277777777778in"
height="3.057638888888889in"}

## Enable repository

\# yum-config-manager \--enable \<repo\>

![](images/media/image19.png){width="5.992361111111111in"
height="0.8402777777777778in"}

![](images/media/image20.png){width="5.989583333333333in"
height="3.1645833333333333in"}

## Disable repository

\# yum-config-manager \--disable \<repo\>

![](images/media/image21.png){width="5.998611111111111in"
height="3.0034722222222223in"}

## View history

\# yum history

![](images/media/image22.png){width="5.991666666666666in"
height="0.8673611111111111in"}

## Undo a history transaction

\# yum history undo \<ID\>

![](images/media/image23.png){width="5.991666666666666in"
height="2.595138888888889in"}

![](images/media/image24.png){width="5.99375in"
height="3.390972222222222in"}

![](images/media/image25.png){width="5.988888888888889in"
height="0.9895833333333334in"}

## Redo a history transaction

\# yum history redo \<ID\>

![](images/media/image26.png){width="5.991666666666666in"
height="2.779166666666667in"}

![](images/media/image27.png){width="5.9944444444444445in"
height="1.15in"}

![](images/media/image28.png){width="5.9944444444444445in"
height="0.9701388888888889in"}

## Clean cache

\# yum clean all

![](images/media/image29.png){width="4.9in"
height="0.9416666666666667in"}

## Install specific package from repo

\# yum \--enablerepo=\<repo\> install \<package\>

![](images/media/image30.png){width="5.988194444444445in"
height="2.467361111111111in"}

![](images/media/image31.png){width="5.992361111111111in"
height="2.5097222222222224in"}

# 

# 
