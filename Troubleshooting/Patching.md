Patching

1\. What is Patching?

Patching means applying updates to the operating system or software to
fix bugs, close security holes, or add features.

Example: Updating packages using yum, installing packages, and applying
Linux software and kernel updates.

2\. Types of Patching

Security Patching:

• Security team scans packages weekly and provides reports. OS packages
are scanned once every 3 months.

• Purpose: Fix security vulnerabilities or loopholes that could be
exploited by attackers.

• Severity:

\- High = Fix high priority issues

\- Medium = Medium priority issues

\- Low = Low priority issues

• Frequency: Often released urgently or monthly.

• Examples: OS security updates, antivirus definitions, CVE fixes.

Normal or Regular Patching:

• Purpose: Improve stability, fix bugs, or enhance features (not
security-focused).

• Frequency: Periodic vendor-released updates.

• Examples: Minor version updates, bug fixes, driver updates.

Complete Patch (Full/Service Pack or Cumulative Update):

• Purpose: A comprehensive update with all previous patches (security +
functional) and major changes.

• Frequency: Less frequent, usually after major releases.

• Examples: Windows Service Packs, cumulative patches, firmware updates.

3\. Verify OS Version and Release

cat /etc/os-release:

![](images/media/image1.tmp){width="4.340500874890639in"
height="2.7987554680664917in"}

• Displays detailed OS information.

• Works on most modern Linux distributions.

• Output includes:

\- NAME

\- VERSION

\- ID

\- PRETTY_NAME

\- VERSION_ID

cat /etc/redhat-release:

• Shows OS version (one line).

• Used in RHEL/CentOS/Fedora.

![](images/media/image2.tmp){width="3.4515660542432194in"
height="0.37501968503937005in"}

hostnamectl:

• Displays system information including OS version, kernel,
architecture.

![](images/media/image3.tmp){width="4.291887576552931in"
height="2.6112456255468066in"}

4\. Practical Work: Patching, Updates, and Installing Packages

Dry Run:

A dry run downloads and stores packages in cache without installing
them.

Edit yum config:

vi /etc/yum.conf

Add:

tsflags=test

This simulates the transaction without actual installation.

![](images/media/image4.tmp){width="2.930706474190726in"
height="0.3125164041994751in"}

![](images/media/image5.tmp){width="2.9932097550306214in"
height="1.9723239282589675in"}

Before that:

yum clean all → Clears stored packages.

![](images/media/image6.tmp){width="2.5973556430446196in"
height="0.5972528433945756in"}

Check for updates:

yum check-update

![](images/media/image7.tmp){width="6.0in"
height="2.7263888888888888in"}

![](images/media/image8.tmp){width="6.0in"
height="3.5708333333333333in"}

Using tsflags=test:

yum update webkit2gtk3-jsc.x86_64

Packages are downloaded and stored in cache but not installed.

![](images/media/image9.tmp){width="2.444570209973753in"
height="0.24306758530183728in"}

![](images/media/image10.tmp){width="6.0in"
height="2.798611111111111in"}

Without tsflags=test:

Remove tsflags=test from /etc/yum.conf

![](images/media/image11.tmp){width="2.9029265091863516in"
height="0.2777919947506562in"}

![](images/media/image12.tmp){width="3.3612839020122482in"
height="2.069550524934383in"}

Then run:

yum update

![](images/media/image13.tmp){width="6.0in"
height="2.6319444444444446in"}

![](images/media/image14.tmp){width="6.0in"
height="2.7819444444444446in"}

Downloaded packages are stored under:

/var/cache/dnf/appstream/packages/

![](images/media/image15.tmp){width="6.0in"
height="0.5541666666666667in"}

Once updated, they will no longer appear in the cache.
