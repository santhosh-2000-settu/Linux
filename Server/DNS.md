# DNS Server Configuration (BIND)

• DNS translates the human-friendly domain name into an IP

address (like 93.184.216.34) so your browser can connect to the

right server. It is called forward lookup zone (A)

• DNS can also do the reverse: mapping an IP address → domain

name. It is called reverse lookup (PTR)

• [PORT NUMBER 53]{.mark}

• Service name : [named]{.mark}

• Package required : bind bind-utils

## Step 1: Install bind and bind-utils packages

These packages are required to configure a DNS server.

\- bind: The main DNS server package.

\- bind-utils: Provides tools such as \*dig\*, \*nslookup\*, \*host\*,
etc.

Command:

yum install bind bind-utils

![](media/image1.tmp){width="6.0in" height="1.2118055555555556in"}

Enable the service after installing

![](media/image2.tmp){width="3.4862904636920384in"
height="0.39585411198600173in"}

## Step 2: Modify /etc/named.conf file

This is the main configuration file of the BIND DNS server.

You remove unnecessary lines from logging to root.key to keep the file
clean.

![A screen shot of a computer code AI-generated content may be
incorrect.](media/image3.tmp){width="4.791666666666667in"
height="3.066666666666667in"}

Command:

vim /etc/named.conf

![](media/image4.tmp){width="3.1321052055993in"
height="0.24306758530183728in"}

![](media/image5.tmp){width="6.0in" height="4.094444444444444in"}

## Step 3: Append rfc1912 zones file

This file contains standard recommended DNS zone configurations.

Appending it adds default zone configurations.

Command:

cat /etc/named.rfc1912.zones \>\> /etc/named.conf

![](media/image6.tmp){width="5.396111111111111in"
height="0.38890857392825895in"}

• The file /etc/named.rfc1912.zones contains predefined zone

configurations for common zones

• You import those default common zones into named.conf

## 

## Step 4: Update named.conf with custom options

You configure:

\- The IP addresses the DNS will listen on (53 is DNS port)

\- The directory for DNS zone files

\- Allow DNS queries from all clients

\- Create a custom zone called glotech.com

![](media/image7.tmp){width="3.041823053368329in"
height="0.36112970253718285in"}

Configuration added:

options {

listen-on port 53 { 127.0.0.1; 192.168.44.10; };

allow-query { localhost; any; };

};

![](media/image8.tmp){width="5.507227690288714in"
height="1.9237095363079615in"}

zone \"glotech.com\" IN {

type master;

file \"forward_zone\";

};

![](media/image9.tmp){width="2.77792104111986in"
height="1.027830271216098in"}

## Step 5: Create forward zone file

This file will store DNS records for glotech.com.

We copy a sample file (named.localhost) to use as a template.

Commands:

cd /var/named

cp named.localhost forward_zone

![](media/image10.tmp){width="4.368279746281715in"
height="0.39585411198600173in"}

## Step 6: Change ownership of the zone file

The named service needs permission to read the zone file.

So, ownership is changed to the \*named\* user.

Command:

chown named:named forward_zone

![](media/image11.tmp){width="5.166932414698163in"
height="4.187715441819773in"}

## Step 7: Modify forward_zone file

DNS records are added for the domain and hostnames.

![](media/image12.tmp){width="3.1876640419947506in"
height="0.34723972003499565in"}

Example records:

glotech.com. IN A 192.168.44.10

server IN A 192.168.44.10

client IN A 192.168.44.11

\...

![](media/image13.tmp){width="4.9655325896762905in"
height="1.8820406824146982in"}

SOA and NS records define the authority and the nameserver for the zone.

## Step 8: Update /etc/resolv.conf

This configures the system to use the newly created DNS server.

![](media/image14.tmp){width="3.5487937445319333in"
height="0.19445428696412947in"}

Content:

search glotech.com

nameserver 192.168.44.10

![](media/image15.tmp){width="2.7084722222222224in"
height="0.7083694225721785in"}

## Step 9: Restart DNS service

You restart and enable DNS so it runs on boot.

Commands:

systemctl restart named

systemctl enable named

![](media/image16.tmp){width="3.319615048118985in"
height="0.22917869641294839in"}

![](media/image17.tmp){width="3.4376771653543305in"
height="0.16667541557305338in"}

## Step 10: Client-side configuration

Each client must point to the new DNS server by updating
/etc/resolv.conf.

![](media/image18.tmp){width="3.25711176727909in"
height="0.2847364391951006in"}

Content:

search glotech.com

nameserver 192.168.44.10

![](media/image19.tmp){width="3.1529396325459316in"
height="0.7639282589676291in"}

## Validation

To test DNS resolution:

Commands:

host glotech.com

nslookup glotech.com

![](media/image20.tmp){width="4.687740594925634in"
height="1.9375995188101487in"}

Client side output:

![](media/image21.tmp){width="6.0in" height="3.259027777777778in"}

![](media/image22.tmp){width="3.312670603674541in"
height="1.6459175415573053in"}

If results show the correct IPs, DNS is workin

This completes the DNS server configuration using BIND.
