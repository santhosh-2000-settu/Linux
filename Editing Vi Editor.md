# Editing Vi Editor

• vi (Visual Editor) is one of the most widely used text editors in
Linux/Unix systems.

• It's terminal-based (runs in the shell) and very powerful once you
know the commands.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Modes in vi

vi mainly has three modes:

1\. Command Mode (default)

• Used for navigation, deleting, copying, saving, quitting, etc.

• Keys are interpreted as commands.

• Example: dd deletes a line.

2\. Insert Mode

• Used to actually type and edit text.

• Enter insert mode from command mode by pressing:

\- i → insert at cursor

\- a → append after cursor

\- o → open a new line below

• Press Esc to return to Command Mode.

3\. Execution Mode

## Command Mode

• Default mode when you open a file with vi filename.

• In this mode, every key you press is treated as a command, not as text
input.

• You can navigate, delete, copy, paste, search, and run commands, but
you cannot type text directly.

• To type/edit text, you must switch to Insert Mode.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### How to Enter Command Mode

• When you open a file in vi, you are already in Command Mode.

• If you're not sure, press Esc → this always brings you back to Command
Mode

**Common Command Mode Actions**

Action Command (in Command Mode)

Delete current line Dd

![](images/media/image1.png){width="4.841666666666667in"
height="5.941666666666666in"}

Delete word Dw

![](images/media/image2.png){width="3.966666666666667in"
height="4.941666666666666in"}

Copy line Yy

![](images/media/image3.png){width="3.966666666666667in"
height="1.5083333333333333in"}

Paste P

![](images/media/image4.png){width="3.925in"
height="1.2583333333333333in"}

Undo last change U

![](images/media/image5.png){width="4.208333333333333in"
height="4.933333333333334in"}

Redo Ctrl+r

![](images/media/image6.png){width="5.233333333333333in"
height="4.975in"}

Search for a word /word

![](images/media/image7.png){width="4.691666666666666in"
height="5.216666666666667in"}

Replace first occurrence in line :s/old/new

![](images/media/image8.png){width="4.875in"
height="5.158333333333333in"}

Replace all occurrences in line :s/old/new/g

Replace in whole file :%s/old/new

Save :shift +zz or ZZ

![](images/media/image9.png){width="5.766666666666667in"
height="3.0430555555555556in"}

Quit :q

Save & Quit :wq

![](images/media/image10.png){width="5.763888888888889in"
height="2.6756944444444444in"}

## Insert Mode

🔹 What is Insert Mode?

• Insert Mode is where you actually type and edit text in vi.

• When you open a file, you start in Command Mode (where keys are
commands).

• To type normal text, you must switch into Insert Mode.

• Once in Insert Mode, the keys you press are inserted into the file
(just like in a normal editor).

### How to Enter Insert Mode

Command Action

i Insert before the cursor

![](images/media/image11.png){width="5.7652777777777775in"
height="5.9375in"}

I Insert at the beginning of the current line

![](images/media/image12.png){width="5.768055555555556in"
height="4.483333333333333in"}

a Append (insert after the cursor).

![](images/media/image13.png){width="5.761805555555555in"
height="4.848611111111111in"}

A Append at the end of the current line.

![](images/media/image14.png){width="4.625in"
height="6.483333333333333in"}

O Open a new line below the current line and enter insert mode.

![](images/media/image15.png){width="5.125in" height="5.4in"}

O Open a new line above the current line and enter insert mode.

![](images/media/image16.png){width="5.766666666666667in"
height="4.679861111111111in"}

After editing, press Esc to go back to command mode.

## Execution Mode

Ex Mode is accessed by typing : in command mode.

### Ex Mode Commands in Vim

  ----------------------------------- -----------------------------------
  Command                             Meaning / Function

  ----------------------------------- -----------------------------------

![](images/media/image17.png){width="4.725in" height="6.575in"}
