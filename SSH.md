# SSH (Secure Shell or Secure Socket Shell)

SSH is a protocol used to securely connect to remote servers. The
default port number is 22.\
Commands to view IP address:\
• ip a

![](images/media/image1.png){width="5.7652777777777775in"
height="1.6881944444444446in"}

• ifconfig

![](images/media/image2.png){width="5.7659722222222225in"
height="2.8041666666666667in"}

• ip addr

![](images/media/image3.png){width="5.764583333333333in"
height="1.6944444444444444in"}

To change hostname:\
\# hostnamectl set-hostname \<new-hostname\>

![](images/media/image4.png){width="5.761805555555555in"
height="3.1847222222222222in"}

Important configuration files:\
• /etc/ssh/sshd_config\
• /etc/ssh/ssh_config\
\
To change the port number or other configuration settings,

#vi /etc/ssh/sshd_config and restart the service:

![](images/media/image5.png){width="5.759722222222222in"
height="1.40625in"}

![](images/media/image6.png){width="5.760416666666667in"
height="1.2618055555555556in"}

\# systemctl restart sshd

![](images/media/image7.png){width="5.7652777777777775in"
height="0.5270833333333333in"}

SSH Login syntax:\
\# ssh \<username\>@\<server.IP or server name\>

![](images/media/image8.png){width="5.763194444444444in"
height="1.0972222222222223in"}

By default, direct root login is not allowed for security reasons.

# Secure Copy (SCP)

SCP is used to securely copy files between local and remote systems.\
Basic syntax:\
\# scp \<options\> \<source\> \<destination\>

Example to copy a file from a remote server to local:\
\# scp root@92.11.11.128:/root/filename /local/destination/\
\
To enable verbose mode:\
\# scp -v \<source\> \<destination\>

# SSH Key Generation and Authentication

SSH supports key-based authentication using a pair of keys: public and
private.\
To generate keys:\
\# ssh-keygen

![](images/media/image9.png){width="5.7659722222222225in"
height="3.5569444444444445in"}

![](images/media/image10.png){width="2.908333333333333in"
height="0.6in"}

To share the public key with a remote server for passwordless login:\
\# ssh-copy-id -i /root/.ssh/id_rsa.pub user@server_ip

The -i option specifies the identity file (public key) to use.\
To copy a public key to a specific file on the remote server:\
\# scp /root/.ssh/id_rsa.pub
root@192.168.111.129:/home/centos/.ssh/authorized_keys\
This places the public key in the remote user's authorized_keys file,
enabling key-based authentication.
