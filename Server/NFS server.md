#  NFS (Network File System) 

## Introduction

Network File System (NFS) is a protocol that enables the sharing of
files and directories across systems on a network. It is especially
useful for distributing large sets of files among multiple devices
efficiently.\
\
Purpose: File sharing over a network\
Default Port: 2049

## Server Configuration Steps

### 1. Install NFS Utilities

Install the required NFS package:

- \# yum install nfs-utils

  ![](images/media/image1.tmp){width="6.0in"
  height="0.7506944444444444in"}

Check the rpcbind service status:

- \# systemctl status rpcbind.service

  ![](images/media/image2.tmp){width="6.0in"
  height="2.1645833333333333in"}

### 2. Disable SELinux

SELinux (Security-Enhanced Linux) enforces strict access controls that
may interfere with NFS operations. To disable it:

- \# vi /etc/selinux/config

Change SELINUX=enforcing to SELINUX=disabled

![](images/media/image3.tmp){width="6.0in"
height="2.6534722222222222in"}

Check the SELinux status:

- \# sestatus

  ![](images/media/image4.tmp){width="4.11132217847769in"
  height="1.9237095363079615in"}

### 3. Enable the NFS Service

Enable and start the NFS service:

- \# systemctl enable \--now nfs-server.service

  ![](images/media/image5.tmp){width="6.0in"
  height="0.22083333333333333in"}

### 4. Create a Shared Directory

Create the directory to be shared (for example, /sharedata):

- \# mkdir /sharedata

  ![](images/media/image6.tmp){width="3.00709864391951in"
  height="0.26390201224846893in"}

### 5. Configure NFS Exports

Edit the exports configuration file:

- \# vi /etc/exports

Add an entry for your client:

- /data client-IP(rw,sync,no_root_squash)

  ![](images/media/image7.tmp){width="5.375276684164479in"
  height="5.347496719160105in"}

### 6. Export the Shared Directory

- \# exportfs -rav

  ![](images/media/image8.tmp){width="6.0in"
  height="0.5340277777777778in"}

- \# exportfs -v

  ![](images/media/image9.tmp){width="6.0in"
  height="0.3736111111111111in"}

### 7. Verify the Export

Check exported directories:

- \# showmount -e

  ![](images/media/image10.tmp){width="3.7640824584426946in"
  height="0.7014249781277341in"}

### 8. Disable Firewall and SELinux Temporarily

To avoid access issues during setup:

- \# systemctl disable \--now firewalld.service

- \# setenforce 0

- \# getenforce

  ![](images/media/image11.tmp){width="4.986367016622922in"
  height="0.9236581364829396in"}

## Client Configuration Steps

### 1. Install NFS Utilities

- \# yum install nfs-utils

  ![](images/media/image12.tmp){width="6.0in"
  height="2.057638888888889in"}

### 2. Check Available Exports

- \# showmount -e server_IP

  ![](images/media/image13.tmp){width="3.7571380139982504in"
  height="0.5416940069991251in"}

### 3. Create a Mount Point

- \# mkdir /dir_name

  ![](images/media/image14.tmp){width="2.465404636920385in"
  height="0.39585411198600173in"}

### 4. Mount the Shared Directory

- \# mount server_IP:/dir_name(server) /dir_name(client)

  ![](images/media/image15.tmp){width="4.458562992125985in"
  height="0.451411854768154in"}

### 5. Verify Mount

- \# df -h

  ![](images/media/image16.tmp){width="6.0in"
  height="1.3458333333333334in"}

### 6. Test File Creation

Create a file in the mounted directory and verify that it appears on the
server.

![](images/media/image17.tmp){width="2.6876377952755908in"
height="0.7222594050743657in"}

Same file should appear in server

![](images/media/image18.tmp){width="2.1251093613298337in"
height="0.4027985564304462in"}

## Root Access Options in NFS

  -----------------------------------------------------------------------
  Option            Client Root       Security Risk     Description
                    Privileges on                       
                    Server                              
  ----------------- ----------------- ----------------- -----------------
  root_squash       None (mapped to   Low (secure)      Disables root
                    \"nobody\")                         privileges from
                                                        clients.

  no_root_squash    Full root         High (risky)      Grants root
                    privileges                          access; use only
                                                        for trusted
                                                        clients.
  -----------------------------------------------------------------------

root_squash → Safer; prevents remote root access.\
no_root_squash → Grants full root permissions; use cautiously.

## Testing Behavior

• If no_root_squash is configured, files created on the client will
appear on the server.\
• If root_squash is set, the client cannot create files on the server's
shared directory.

![](images/media/image19.tmp){width="5.944749562554681in"
height="5.000256999125109in"}

You cant create a file in client mechine

![](images/media/image20.tmp){width="3.7571380139982504in"
height="0.5486395450568679in"}
