# Schedule Task : Cron Command

## What is cron Command?

The cron tool allows Linux users to execute commands or scripts at a
specific date and time. It is very useful to perform regular tasks such
as backups, daily scans, /tmp directory cleanup, and restarting the
system at a given time.\
\
cron executes scheduled jobs automatically in the background at the
specified time. Each user can have their own crontab, stored under
/var/spool/cron/username.\
\
Cron jobs can be allowed or disallowed for specific users by adding
their username to the \'cron.allow\' or \'cron.deny\' files.

## 1. Cron Package Installation

\# yum install cronie (or) \# yum install crontabs

![](images/media/image1.png){width="5.9944444444444445in"
height="1.44375in"}

## Service Name

The service that runs cron jobs is called crond.\
Check its status with:\
systemctl status crond\
It should show Active: active (running).

![](images/media/image2.png){width="5.988194444444445in"
height="2.6333333333333333in"}

And create edit script file

![](images/media/image3.png){width="3.9833333333333334in"
height="0.325in"}

![](images/media/image4.png){width="5.308333333333334in"
height="6.725in"}

Now give executable permission to the script file

![](images/media/image5.png){width="5.991666666666666in"
height="3.7840277777777778in"}

![](images/media/image6.png){width="5.997916666666667in"
height="3.8465277777777778in"}

And now run the script fie:

To run a script file

\# ./scriptfile

![](images/media/image7.png){width="5.992361111111111in"
height="3.803472222222222in"}

## Edit Crontab Entries

Use: crontab -e

![](images/media/image8.png){width="4.141666666666667in"
height="0.38333333333333336in"}

![](images/media/image9.png){width="4.975in"
height="6.141666666666667in"}

Example entries:\
\* \* \* \* \* script.sh \> /tmp/script_out -- runs every minute\
\*/5 \* \* \* \* -- runs every 5 minutes\
0 10 \* \* \* -- runs every day at 10:00\
30 1 \* \* \* -- runs daily at 01:30\
30 1,4,5 1-10 \* \* -- runs at 01:30 on days 1--10 of the month and also
at 04:30 and 05:30 during those days\
\
Special strings:\
\@daily -- once per day\
\@reboot -- on system startup\
\@hourly -- once per hour\
\@yearly -- once per year

## List Existing Cron Jobs

crontab -l

![](images/media/image10.png){width="4.066666666666666in"
height="0.675in"}

## Remove Crontab Entry

crontab -r

![](images/media/image11.png){width="3.9166666666666665in"
height="0.3416666666666667in"}

And run scheduled scriptfile

![](images/media/image12.png){width="5.995138888888889in"
height="3.4402777777777778in"}

![](images/media/image13.png){width="5.995833333333334in"
height="1.5479166666666666in"}

To view live process:

\# watch cat scriptfilename

![](images/media/image14.png){width="5.133333333333334in"
height="0.35833333333333334in"}

![](images/media/image15.png){width="5.991666666666666in"
height="4.5777777777777775in"}

## Edit Crontab for a Different User

crontab -u username -e \# edit\
crontab -u username -r \# remove\
crontab -u username -l \# list

## General Syntax of a Cron Job

MIN HOUR DayOfMonth Month DayOfWeek Command\
0-59 0-23 1-31 1-12 0-6 Any Linux command or script

## Important Notes

\- User crontab files are stored in /var/spool/cron/username.\
- Cron jobs run using the system timezone. Ensure it matches your
expectation.\
- If the user account or password is expired, cron jobs for that user
will not run.\
- If the crond service is stopped, cron jobs will not run.\
- If the /var filesystem reaches 100% usage, cron jobs will fail because
cron cannot write logs or PID files.
