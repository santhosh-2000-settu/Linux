Apache Server

Install httpd package:

#yum install httpd

![](media/image1.tmp){width="5.768055555555556in"
height="2.6972222222222224in"}

![](media/image2.png){width="5.768055555555556in"
height="0.6027777777777777in"}

Enable httpd package:

#systemctl enable \--now httpd

![](media/image3.png){width="5.768055555555556in" height="0.36875in"}

Check Status:

#systemctl status httpd

![](media/image4.tmp){width="5.768055555555556in"
height="1.8729166666666666in"}

Test page:

Copy ip address.

Test in browser.

![](media/image5.tmp){width="5.768055555555556in"
height="2.9027777777777777in"}

![](media/image6.png){width="5.768055555555556in"
height="3.6166666666666667in"}

Change directory:

#cd /var/www/html/

#vi index.html

![](media/image7.tmp){width="3.229332895888014in"
height="0.48613626421697287in"}

HTML content:

![](media/image8.tmp){width="3.2779461942257218in"
height="1.8612062554680664in"}

Restart package:

#systemctl restart httpd

![](media/image9.tmp){width="3.680744750656168in"
height="0.4375229658792651in"}

View the html content using cat command:

#cat /var/www/html/index.html

![](media/image10.tmp){width="4.11132217847769in"
height="2.1459437882764654in"}

To view installed package:

#rpm -qa\|grep httpd

![](media/image11.tmp){width="3.25711176727909in"
height="1.3889599737532807in"}

To view all files from installed httpd-core package:

#rpm -ql httpd-core-2.4.62-7.el9.x86_64\|grep vhost

![](media/image12.tmp){width="5.768055555555556in"
height="0.7458333333333333in"}

#cat /usr/share/doc/httpd-core/httpd-vhosts.conf

![](media/image13.tmp){width="4.48634186351706in"
height="5.153042432195975in"}

Copy code:

\<VirtualHost \*:80\>

ServerAdmin webmaster@dummy-host.example.com

DocumentRoot \"/var/www/dummy-host.example.com\"

ServerName dummy-host.example.com

ServerAlias www.dummy-host.example.com

ErrorLog \"/var/log/httpd/dummy-host.example.com-error_log\"

CustomLog \"/var/log/httpd/dummy-host.example.com-access_log\" common

\</VirtualHost\>

#cd /etc/httpd/

#ll

![](media/image14.tmp){width="5.768055555555556in"
height="1.7048611111111112in"}

#cd /etc/httpd/conf.d

#vi manju.com.conf\_

![](media/image15.tmp){width="3.6738003062117235in"
height="0.4236329833770779in"}

Paste code.

![](media/image16.tmp){width="5.507227690288714in"
height="2.257060367454068in"}

#vi /etc/hosts

Machine_Ip_address website_name

![](media/image17.tmp){width="5.768055555555556in"
height="0.9159722222222222in"}

Restart package:

#systemctl restart httpd.

![](media/image18.tmp){width="3.8613090551181104in"
height="0.4375229658792651in"}

Test website with curl command:

#curl [www.krish.com](http://www.manju.com)

![](media/image19.tmp){width="3.7640824584426946in"
height="2.180667104111986in"}

Test in browser:

Open [www.krish.com](http://www.krish.com)

![](media/image20.tmp){width="5.768055555555556in"
height="1.8576388888888888in"}
