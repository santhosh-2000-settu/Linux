# Services & Daemons

Daemons are programs that run in the background performing various
tasks.

## Start and Stop services

\# systemctl start crond

![](images/media/image1.png){width="5.9944444444444445in"
height="1.6277777777777778in"}

\# systemctl stop crond

![](images/media/image2.png){width="5.999305555555556in"
height="1.2534722222222223in"}

## Restart and Reload services

\# systemctl restart crond

![](images/media/image3.png){width="5.999305555555556in"
height="1.9006944444444445in"}\
\
To reload all the configuration files forcefully on your system:\
\# systemctl reload crond

![](images/media/image4.png){width="5.998611111111111in"
height="2.091666666666667in"}

To view complete log

#systemctl journal -xeu service name

![](images/media/image5.png){width="5.999305555555556in"
height="2.7055555555555557in"}

## Enable and Disable services

\# systemctl enable crond

![](images/media/image6.png){width="5.995138888888889in"
height="2.077777777777778in"}\
\
\
\# systemctl disable crond

![](images/media/image7.png){width="5.998611111111111in"
height="2.1979166666666665in"}

To permanently enable or disable:\
\
\
\# systemctl enable sshd --now

![](images/media/image8.png){width="5.995833333333334in"
height="2.1006944444444446in"}

\# systemctl disable sshd --now

![](images/media/image9.png){width="5.995833333333334in"
height="2.089583333333333in"}

\# systemctl is-active sshd

![](images/media/image10.png){width="5.966666666666667in"
height="0.6333333333333333in"}

\# systemctl is-enabled sshd

![](images/media/image11.png){width="6.0in"
height="0.6166666666666667in"}

## List Services

List all services:\
\# systemctl list-units \--type service --all

![](images/media/image12.png){width="5.995138888888889in"
height="0.28888888888888886in"}

![](images/media/image13.png){width="5.991666666666666in"
height="2.563888888888889in"}

\# systemctl list-unit-files \--type=service

![](images/media/image14.png){width="5.99375in"
height="0.27291666666666664in"}

![](images/media/image15.png){width="5.996527777777778in"
height="3.8333333333333335in"}

List of services that are active now:\
\# systemctl -t service

![](images/media/image16.png){width="5.333333333333333in"
height="0.31666666666666665in"}

![](images/media/image17.png){width="5.991666666666666in"
height="2.740972222222222in"}
