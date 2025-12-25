# Overview

It helps to create a local or FTP-based YUM repository on a RHEL/CentOS
8 system using package directories. This is useful for systems without
internet access, enabling installation of software packages directly
from a local or FTP source.

#  Copy Packages

First, create directories to hold the AppStream and BaseOS packages and
copy them from :\
Commands:\
\# mkdir /var/ftp/pub/AppStream\
\# mkdir /var/ftp/pub/BaseOS

![](images/media/image1.png){width="5.996527777777778in"
height="0.6319444444444444in"}\
\
\# cp -rv AppStream/Packages /var/ftp/pub/AppStream/\
\# cp -rv BaseOS/Packages /var/ftp/pub/BaseOS/

![](images/media/image2.png){width="5.993055555555555in"
height="0.1763888888888889in"}

Explanation:\
- mkdir: Creates directories for storing packages.\
- cp -rv: Copies the Packages directories from the mounted to the FTP
directory while showing progress.

# Install createrepo 

If the \'createrepo\' tool is not installed, install it along with
dependencies:\
\# cd /iso/AppStream/Packages\
\# rpm -ivh createrepo_c-0.11.0-1.el8.x86_64.rpm
createrepo_c-libs-0.11.0-1.el8.x86_64.rpm drpm-0.3.0-14.el8.x86_64.rpm\
\
Once installed, create the repository metadata:\
\# createrepo -v /var/ftp/pub/AppStream/Packages/

![](images/media/image3.png){width="5.995833333333334in"
height="0.37777777777777777in"}

![](images/media/image4.png){width="5.992361111111111in"
height="2.5854166666666667in"}

\# createrepo -v /var/ftp/pub/BaseOS/Packages/

![](images/media/image5.png){width="5.997222222222222in"
height="0.3055555555555556in"}

![](images/media/image6.png){width="5.999305555555556in"
height="1.0881944444444445in"}

Explanation:\
- rpm -ivh: Installs RPM packages.\
- createrepo: Generates the required metadata for the YUM repository.

# Create Repository Configuration File

Create a .repo file inside /etc/yum.repos.d/ to define the repository:\
\# cd /etc/yum.repos.d

![](images/media/image7.png){width="5.998611111111111in"
height="0.4527777777777778in"}

\# vi local.repo\
\
Add the following content:\
\[Localrepo_BaseOS\]\
name=Localrepo_BaseOS\
baseurl=file:///var/ftp/pub/BaseOS/Packages\
enabled=1\
gpgcheck=0\
\
\[Localrepo_AppStream\]\
name=Localrepo_AppStream\
baseurl=file:///var/ftp/pub/AppStream/Packages\
enabled=1\
gpgcheck=0

![](images/media/image8.png){width="5.996527777777778in"
height="2.553472222222222in"}

Explanation:\
- baseurl: Points to the local directory where the packages are stored.\
- enabled=1: Enables the repository.\
- gpgcheck=0: Disables GPG key checking for simplicity.

And clear cache:

![](images/media/image9.png){width="5.75in"
height="0.6583333333333333in"}

And then install package:

![](images/media/image10.png){width="5.988194444444445in"
height="2.7895833333333333in"}

![](images/media/image11.png){width="5.998611111111111in"
height="1.4909722222222221in"}

# Optional: FTP-based Repository

If serving packages over FTP:\
\
\# vi /etc/vsftpd/vsftpd.conf\
Set \'anonymous_enable=YES\' to allow anonymous access.

![](images/media/image12.png){width="5.992361111111111in"
height="2.813888888888889in"}

![](images/media/image13.png){width="5.999305555555556in"
height="2.9118055555555555in"}

Now you have to turnoff firewall:

#systemctl disable --now firewalld.service

![](images/media/image14.png){width="5.996527777777778in"
height="0.5118055555555555in"}

#setenforce0

![](images/media/image15.png){width="5.558333333333334in"
height="0.2833333333333333in"}

And enable vstfpd:

#systemctl enable \--now vstfpd

![](images/media/image16.png){width="5.999305555555556in"
height="0.4166666666666667in"}

And then create a directory on clint mechine to install packages from
server:

![](images/media/image17.png){width="5.986805555555556in"
height="1.4in"}

\# systemctl start vsftpd; systemctl enable vsftpd\
\
Create FTP repo entries:\
\[FTPrepo_BaseOS\]\
name=FTPrepo_BaseOS\
baseurl=ftp://192.168.170.165/pub/BaseOS/Packages\
enabled=1\
gpgcheck=0\
\
\[FTPrepo_AppStream\]\
name=FTPrepo_AppStream\
baseurl=ftp://192.168.170.165/pub/AppStream/Packages\
enabled=1\
gpgcheck=0

![](images/media/image18.png){width="5.9944444444444445in"
height="3.6194444444444445in"}

Explanation:\
- vsftpd: Installs FTP server.\
- baseurl: Uses FTP URL pointing to the server\'s IP and package path.

And install the package on client mechine:

\# yum install vsftpd

![](images/media/image19.png){width="5.995833333333334in"
height="2.59375in"}

![](images/media/image20.png){width="5.990972222222222in"
height="1.9041666666666666in"}
