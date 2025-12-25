# 1. useradd -- Create a New User

useradd -g groupname username → Assigns primary group to the user

![](images/media/image1.png){width="5.763888888888889in"
height="0.3215277777777778in"}

useradd -u UID username → Creates user with a custom UID

![](images/media/image2.png){width="5.761111111111111in"
height="1.9229166666666666in"}

useradd -c \"comment\" username → Adds a comment/purpose (stored in
/etc/passwd)

![](images/media/image3.png){width="5.763888888888889in"
height="1.804861111111111in"}

useradd -d /custom/home username → Sets a custom home directory

![](images/media/image4.png){width="5.758333333333334in"
height="1.84375in"}

useradd -s /bin/sh username → Sets a default shell (e.g., bash, sh,
etc.)

![](images/media/image5.png){width="5.756944444444445in"
height="1.8055555555555556in"}

useradd -M username → Creates a user without a home directory

![](images/media/image6.png){width="5.767361111111111in"
height="1.8041666666666667in"}

useradd -e \"YYYY-MM-DD\" username → Sets an expiry date (temporary
user)

![](images/media/image7.png){width="5.763888888888889in"
height="0.30277777777777776in"}

![](images/media/image8.png){width="5.767361111111111in"
height="0.38055555555555554in"}

Example (combine options):

useradd -u 1u500 -g developers -c \"Project User\" -d /data/user1 -s
/bin/bash -e \"2025-12-31\" username

![](images/media/image9.png){width="5.759722222222222in"
height="1.5590277777777777in"}

# 2. usermod -- Modify Existing Users

usermod -l newname oldname → Change login name (username only, UID
remains)

![](images/media/image10.png){width="5.7652777777777775in"
height="2.7006944444444443in"}

usermod -u newUID username → Change UID (must be unused)

![](images/media/image11.png){width="5.767361111111111in"
height="2.6013888888888888in"}

usermod -g newGID username → Change primary group

![](images/media/image12.png){width="5.7659722222222225in"
height="2.6930555555555555in"}

usermod -c \"new comment\" username → Change comment/purpose

![](images/media/image13.png){width="5.763888888888889in"
height="2.823611111111111in"}

usermod -d /new/home username → Change home directory

![](images/media/image14.png){width="5.761805555555555in"
height="2.59375in"}

usermod -s /bin/sh username → Change default shell

![](images/media/image15.png){width="5.764583333333333in"
height="2.6395833333333334in"}

Example (combine options):

usermod -u 1600 -g admins -c \"Admin User\" -d /opt/admin -s /bin/sh
oldusername

![](images/media/image16.png){width="5.767361111111111in"
height="1.7305555555555556in"}

# 3. Locking and Unlocking Accounts

usermod -L username → Lock account (!! Means account is locked)

![](images/media/image17.png){width="5.766666666666667in"
height="3.48125in"}

usermod -U username → Unlock account

![](images/media/image18.png){width="5.761805555555555in"
height="0.4791666666666667in"}

# 4. chage -- Password and Expiry Management

chage -l username → Show password aging details

![](images/media/image19.png){width="5.7659722222222225in"
height="1.3944444444444444in"}

chage -m 5 username → Set minimum 5 days before password change allowed

![](images/media/image20.png){width="5.768055555555556in"
height="1.0597222222222222in"}

chage -M 90 username → Set maximum 90 days validity for password

![](images/media/image21.png){width="5.757638888888889in"
height="1.0798611111111112in"}

chage -W 10 username → Warn user 10 days before password expiry

![](images/media/image22.png){width="5.7659722222222225in"
height="1.6881944444444446in"}

chage -E \"2026-01-31\" username → Set account expiry date

![](images/media/image23.png){width="5.764583333333333in"
height="1.4868055555555555in"}

chage -d 0 username → Force user to change password at next login

![](images/media/image24.png){width="5.761111111111111in"
height="1.3131944444444446in"}

chage username → Interactive mode to set all values

![](images/media/image25.png){width="5.759722222222222in"
height="2.0972222222222223in"}

# 5. groupmod -- Modify Groups

groupmod -n newname oldname → Rename a group

![](images/media/image26.png){width="5.75625in"
height="2.716666666666667in"}

groupmod -g newGID groupname → Change group ID

![](images/media/image27.png){width="5.7652777777777775in"
height="1.5430555555555556in"}
