# Linux Process Management

## What is a Process

An instance of a program is called a Process. In simple terms, any
command that you give to your Linux machine starts a new process.

## Types of Processes in Linux

1.Foreground Processes: They run on the screen and need input from the
user. For example, Office Programs.\
2.Background Processes: They run in the background and usually do not
need user input. For example, Antivirus.

## To List the Processes

\# top

![](images/media/image1.png){width="5.761805555555555in"
height="2.865972222222222in"}

\# ps -ef

![](images/media/image2.png){width="5.763888888888889in"
height="2.834722222222222in"}

## To list all running processes

\# ps aux \| less

![](images/media/image3.png){width="5.768055555555556in"
height="2.966666666666667in"}

## To list a specific user\'s processes

\# ps -u username

![](images/media/image4.png){width="5.764583333333333in"
height="6.646527777777778in"}

## To customize the output of ps aux

\# ps aux

![](images/media/image5.png){width="5.768055555555556in"
height="2.9631944444444445in"}

OUTPUT\
\
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND\
\
\
\# ps -eo uid,user,pid,ppid,stat,cpu,cmd

![](images/media/image6.png){width="5.433333333333334in"
height="5.608333333333333in"}

## Parent process

In Linux all the processes have a parent process. When the user creates
a process, the kernel process becomes the parent of that process.\
\
Every Linux process has two IDs assigned to it: the Process ID (PID) and
the Parent Process ID (PPID).

To check PID

#pidof command

![](images/media/image7.png){width="5.767361111111111in"
height="0.5388888888888889in"}

To view tree view

#pstree

![](images/media/image8.png){width="5.7555555555555555in"
height="2.988888888888889in"}

## Child Processes

The processes created by another process (its parent process) are known
as child processes.\
In the above example, the sleep process with PID 1971 is a child process
of the bash process with PID 1589.

## Daemon process

The system-related background running processes are called Daemon
Processes. When you see a process running with a \'?\' mark in the sixth
column (TTY field), that\'s a daemon process.

## Zombie processes

At times there are processes which are already dead but still show up in
the process list. These are called Zombie processes. These processes can
be found while doing ps listing. A process with a Z state is a zombie
process. They don\'t consume any CPU resources.

## Process Status Codes

The process status can be any of the following:\
R: Running - Running process executed on CPU.\
S: Sleeping - Waiting process for a signal.\
D: Uninterruptible sleep - Sleeping process which will not respond to a
signal.\
T: Traced (Stopped state) - Process stopped or suspended. It can be
continued by another signal.\
Z: Zombie - A child process that has finished execution but whose parent
has not yet read its exit status.

A Zombie process occurs when a child process sends its parent process an
exit signal but the parent has not called wait() to collect the child\'s
exit code. The child remains as a zombie entry in the process table. It
does not use CPU or memory resources except for a small process table
entry. To clean it up, ensure the parent process properly waits for
child termination or, if needed, terminate or restart the parent so the
init process adopts and reaps the zombie.

# Process Management Commands

1\. Sleep Command\
\# sleep 10 -\> Makes the terminal sleep for 10 seconds.

![](images/media/image9.png){width="4.083333333333333in"
height="0.625in"}

#sleep 10 & -\> Runs the sleep command in the background.

![](images/media/image10.png){width="5.341666666666667in"
height="0.625in"}

#jobs -\> View background running processes.

![](images/media/image11.png){width="5.7652777777777775in"
height="0.6166666666666667in"}

#fg %\[1\] -\> Bring a background job to the foreground (job number
depends on the job id).

![](images/media/image12.png){width="3.6416666666666666in"
height="0.6833333333333333in"}

#Ctrl + C -\> Kill the foreground process.

![](images/media/image13.png){width="2.058333333333333in"
height="0.325in"}

2\. Kill Signals\
\
\* There are 64 kill signals. (List them with: kill -l)

![](images/media/image14.png){width="5.761805555555555in"
height="2.125in"}

\* SIGHUP (1) -\> Hangup signal to cut off a process in the middle (#
kill -1 PID).

![](images/media/image15.png){width="5.708333333333333in"
height="2.658333333333333in"}

\* SIGQUIT (3) -\> Quit and create a core dump (# kill -3 PID).

![](images/media/image16.png){width="5.761111111111111in"
height="1.5791666666666666in"}

\* SIGKILL (9) -\> Forcefully kill a process (# kill -9 PID).

![](images/media/image17.png){width="5.641666666666667in"
height="2.1in"}

\* SIGCONT (18) -\> Continue a stopped process.

![](images/media/image18.png){width="5.575in"
height="1.4916666666666667in"}

\* SIGSTOP (19) or SIGSTP -\> Stop a process.

![](images/media/image19.png){width="5.6in"
height="1.5416666666666667in"}

\* SIGTERM (15) -\> Default termination signal.

![](images/media/image20.png){width="5.675in"
height="3.841666666666667in"}

\* To kill a specific process: \# kill PID

![](images/media/image21.png){width="5.666666666666667in"
height="1.5083333333333333in"}

\* pkill -\> Kill processes by name (e.g., pkill sleep).

![](images/media/image22.png){width="5.7659722222222225in"
height="1.7881944444444444in"}

\* killall -\> Kill all processes with the exact same command name.

![](images/media/image23.png){width="5.763888888888889in"
height="1.9881944444444444in"}

nice value

\* NICE value defines the priority of a process.\
\* Default nice value -\> 0.\
\* Range: -20 (highest priority) to 19 (lowest priority). There are 40
levels.\
\* Priority value starts from 0\
\
Changing Nice Value:\
\* For a running process: \# renice 10 PID

![](images/media/image24.png){width="5.767361111111111in"
height="0.17847222222222223in"}

![](images/media/image25.png){width="5.7652777777777775in"
height="0.8375in"}

![](images/media/image24.png){width="5.767361111111111in"
height="0.17847222222222223in"}

\* For a new process: \# nice -n 10 command\
\* Example

![](images/media/image26.png){width="5.761111111111111in"
height="0.25in"}

\* Changing with top command:

-r to change

![](images/media/image27.png){width="6.0in"
height="0.15833333333333333in"}

K -\> Kill processes directly.\
3. top Command Usage

\* f -\> View fields

![](images/media/image28.png){width="6.0in" height="4.6in"}

![](images/media/image29.png){width="6.0in"
height="2.1972222222222224in"}

\* c -\> See the full command line.

![](images/media/image30.png){width="6.0in"
height="2.957638888888889in"}\
\* d (delay time) -\> Change delay time of top command refresh.

![](images/media/image31.png){width="3.233613298337708in"
height="0.2583552055993001in"}

\* n -\> Change how many processes are shown (default 10).

![](images/media/image32.png){width="5.29212489063867in"
height="0.2583552055993001in"}

![](images/media/image33.png){width="6.0in"
height="1.5506944444444444in"}\
\* u -\> Show processes of a specific user.

![](images/media/image34.png){width="6.0in"
height="3.209722222222222in"}\
Sorting:\
\* T -\> Sort by running time.

![](images/media/image35.png){width="6.0in"
height="3.2118055555555554in"}

\* P -\> Sort by %CPU usage.

![](images/media/image36.png){width="6.0in"
height="2.5965277777777778in"}\
\* M -\> Sort by %MEM usage.

![](images/media/image37.png){width="6.0in" height="3.425in"}\
\* N -\> Sort by PID.

![](images/media/image38.png){width="6.0in" height="2.7125in"}\
\
Color & Display:\
\* z -\> Toggle color.

![](images/media/image39.png){width="6.0in"
height="3.3243055555555556in"}

\* Shift + z -\> Change color highlight.

![](images/media/image40.png){width="6.0in"
height="2.939583333333333in"}

\* Until you quit top, settings remain active.
