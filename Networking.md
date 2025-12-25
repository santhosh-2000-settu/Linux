#  Networking

## IP Address Classes

Class A -- Classful subnet mask is /8. Provides 16,777,216 possible IP
addresses (2\^24).\
Class B -- Classful subnet mask is /16. Provides 65,536 possible IP
addresses.\
Class C -- Classful subnet mask is /24. Provides 256 possible IP
addresses.

## Set Dynamic IP Address

Steps:\
1. Select VM → Settings → Add Network Adapter.

![](images/media/image1.png){width="5.992361111111111in"
height="6.039583333333334in"}\
2. Check the interface name:\
\# ifconfig or #ip a

![](images/media/image2.png){width="5.992361111111111in"
height="2.1131944444444444in"}

\# nmcli device show

![](images/media/image3.png){width="5.9944444444444445in"
height="2.9611111111111112in"}

![](images/media/image4.png){width="5.992361111111111in"
height="2.654861111111111in"}

![](images/media/image5.png){width="5.997916666666667in"
height="2.136111111111111in"}

3\. Connect the interface:\
\# nmcli device connect ens36

![](images/media/image6.png){width="5.997916666666667in"
height="1.0770833333333334in"}

## Set Static IP Address

Steps:\
1. Select VM → Settings → Add Network Adapter.

![](images/media/image7.png){width="5.999305555555556in"
height="6.086805555555555in"}

2\. Check the interface name:\
\# ifconfig or #ip a

![](images/media/image8.png){width="5.988194444444445in"
height="2.120833333333333in"}

![](images/media/image9.png){width="5.988888888888889in"
height="1.2243055555555555in"}

\# nmcli device show

![](images/media/image10.png){width="5.993055555555555in"
height="3.152083333333333in"}

![](images/media/image11.png){width="5.997916666666667in"
height="3.1395833333333334in"}

![](images/media/image12.png){width="5.99375in"
height="3.0215277777777776in"}

\# nmcli connection status

![](images/media/image13.png){width="5.999305555555556in"
height="1.4256944444444444in"}

#nmcl device status

![](images/media/image14.png){width="5.995833333333334in"
height="3.017361111111111in"}

3\. Add static IP configuration:\
\# nmcli con add type ethernet con-name ens160 ifname ens160
ipv4.addresses 192.168.159.51/24 ipv4.gateway 192.168.0.1 autoconnect
yes ipv4.method manual\
\# nmcli con add type ethernet con-name ens160 ifname ens160 ip4
192.168.159.51/24 gw4 192.168.0.1 autoconnect yes ipv4.method manual

![](images/media/image15.png){width="5.988888888888889in"
height="1.136111111111111in"}

#nmcl device show

![](images/media/image16.png){width="5.996527777777778in"
height="2.1847222222222222in"}

## Command to Check Gateway

\# netstat -rn

![](images/media/image17.png){width="5.991666666666666in"
height="1.5902777777777777in"}

\# route -n

![](images/media/image18.png){width="5.995833333333334in"
height="1.6458333333333333in"}

## To list ports:

#netstat -pultan

![](images/media/image19.png){width="5.995833333333334in"
height="1.7520833333333334in"}

## Connection Modify

You have to disconnect the nat before modify

![](images/media/image20.png){width="6.0in"
height="0.6791666666666667in"}

To modify connection parameters:\
\# nmcli con modify ens160 ipv4.addresses 192.168.2.100/24\
\# nmcli con mod ens160 ipv4.gateway 192.168.2.1\
\# nmcli con mod ens160 ipv4.dns 8.8.8.8\
\# nmcli con mod ens160 ipv4.method manual\
\# nmcli con mod ens160 connection.autoconnect yes\
Or combine in one command:\
\# nmcli con modify ens160 ipv4.addresses 192.168.2.100/24 ipv4.gateway
192.168.2.1 ipv4.method manual connection.autoconnect yes

![](images/media/image21.png){width="5.999305555555556in"
height="1.9708333333333334in"}

![](images/media/image22.png){width="5.9944444444444445in"
height="1.25625in"}

## To Monitor IP Packets: iptraf-ng

iptraf-ng is a console-based network monitoring utility for Linux that
provides real-time statistics of network traffic. It displays data like
current connections, protocol distribution, and network interface
statistics. It\'s useful for troubleshooting, performance monitoring,
and identifying unusual network activity.\
\
Usage:\
1. Install the tool: \# yum install iptraf-ng

![](images/media/image23.png){width="5.991666666666666in"
height="2.495833333333333in"}

![](images/media/image24.png){width="5.999305555555556in"
height="2.5125in"}

2\. Run the command: \# iptraf-ng

![](images/media/image25.png){width="3.908333333333333in"
height="0.39166666666666666in"}

![](images/media/image26.png){width="5.991666666666666in"
height="2.85625in"}

3. Use the interactive interface to select interfaces and view detailed
traffic information.

#nmtui

![](images/media/image27.png){width="2.5in"
height="0.31666666666666665in"}

![](images/media/image28.png){width="5.988888888888889in"
height="2.890277777777778in"}

![](images/media/image29.png){width="5.988888888888889in"
height="2.967361111111111in"}

. Use the interactive interface to select interfaces and view detailed
traffic information
