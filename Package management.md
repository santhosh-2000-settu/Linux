#  Package Management

## Overview

There are two ways to install a package in Red Hat-based Linux systems:\
\* RPM (Redhat Package Manager)\
\* YUM (Yellowdog Updater, Modified)\
RPM stands for Redhat Package Manager and uses .rpm files for packages.

## Package Syntax

Format: packagename-Version-Release.architecture.ext\
Example: httpd-2.4.6-97.el7.centos.x86_64.rpm

![](images/media/image1.png){width="5.383333333333334in"
height="0.31666666666666665in"}

## Basic Commands

1.  Check installed block devices:\
    \# lsblk

    ![](images/media/image2.png){width="5.995833333333334in"
    height="1.3701388888888888in"}

2\. List contents of a directory and count words/lines:\
\# ls \| wc (word count)

![](images/media/image3.png){width="5.2in"
height="0.6083333333333333in"}

#ls \| wc -l (line)

![](images/media/image4.png){width="5.691666666666666in"
height="0.65in"}

#ls \| wc -- w (words)

![](images/media/image5.png){width="4.825in" height="0.675in"}

#ls \| wc -c (charecters)

![](images/media/image6.png){width="4.858333333333333in" height="0.4in"}

## Installing Packages

\# rpm -ivh \<packagename\>.rpm\
- Installs a package with verbose and hash progress. All dependencies
must be met.

![](images/media/image7.png){width="5.993055555555555in"
height="0.6583333333333333in"}

## Listing Installed Packages

\# rpm -qa\
- Lists all installed packages.

![](images/media/image8.png){width="5.995138888888889in"
height="4.998611111111111in"}

\# rpm -q \| grep \<package\>\
- Checks if a specific package is installed.

## Checking Dependencies

\# rpm -qpr \<package.rpm\>\
- Lists capabilities and dependencies of an RPM package.

![](images/media/image9.png){width="5.997222222222222in"
height="3.654166666666667in"}

-q : Query a package\
-p : Query an uninstalled package file\
-R : List capabilities on which the package depends

## List Files of Installed Package

\# rpm -ql \<package\>\
- Lists all files installed by a package.

![](images/media/image10.png){width="5.999305555555556in"
height="2.49375in"}

To see last installed date

#rpm -ra --last

![](images/media/image11.png){width="5.998611111111111in"
height="3.1069444444444443in"}

To upgrade

\# rpm -Uvh packagename

![](images/media/image12.png){width="5.989583333333333in"
height="0.6409722222222223in"}

## Removing Packages

\# rpm -evh \<package\>

\- Removes a package.

![](images/media/image13.png){width="5.989583333333333in"
height="0.68125in"}

\# rpm -evh \--nodeps \<package\>\
- Removes a package without removing dependencies.

![](images/media/image14.png){width="5.995833333333334in"
height="1.2791666666666666in"}

## Find Package for a Command

\# rpm -qf /usr/bin/mkdir\
- Finds which package provides a specific command or file.

![](images/media/image15.png){width="5.997916666666667in"
height="0.475in"}

## Query Information of Installed Package

\# rpm -qi \<package\>

![](images/media/image16.png){width="5.999305555555556in"
height="2.922222222222222in"}

\- Displays information about an installed package.\
Example: mkdir\'s package is coreutils.

## Query Before Installing

\# rpm -qlp \<package.rpm\>\
- Lists files in an RPM before installing.

![](images/media/image17.png){width="5.9944444444444445in"
height="3.238888888888889in"}

\# rpm -qdp \<package.rpm\>\
- Lists documentation files in an RPM before installing.

![](images/media/image18.png){width="5.988888888888889in"
height="2.513888888888889in"}

\# rpm -qcp \<package.rpm\>\
- Lists configuration files in an RPM before installing.

![](images/media/image19.png){width="5.99375in"
height="0.33541666666666664in"}

## Query Documentation of Installed Package

\# rpm -qdf \<package\>\
- Lists documentation files installed with a package.

![](images/media/image20.png){width="5.999305555555556in"
height="1.238888888888889in"}
