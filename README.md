# KodeKloud Linux Basics: Working with the Shell Part 1

[KodeKloud Linux Basics Course Notes Table of Contents](https://github.com/pslucas0212/LinuxBasics)


### Linux Command line
The Linux command line is commonly known as the linux shell.  The Linux shell is a prorgam interface between the user and computer.  You use text based commands to interact with the operating system.  When you login you are taken to a computer generated directory known as the home directory.  This is users home folder or directory which is located under /home.  /home is a user generated folder.  The user home directory is generated from the user login id and is unique to each user.  You can store your personal data in the home directory.  Like a dedicate locker where you can read, write and delete personal data.  No other user has access to your home directory.
```
/home/<user name>
```
```
$ pwd
/home/pslucas
```

On the commnand lin promte, the home directory is denoted by a ~ symbol.  The ~ represents the home directory
```
[pslucas@ns02 ~]$
```

When you interact with the shell you type in a command.  On the command line you enter a command like the "echo" command.  
```
$ echo


```
You saw nothing printed becuase you didn't enter an argument with ehco command.  Commands take arguements.  The echo command takes a string text as an argument
```
$ echo 'Hello World'
Hello World
```
Some commands do not need an argument like the "uptime" command which shows how long the system has been running
```
$ uptime
 08:12:02 up 33 days, 18:46,  1 user,  load average: 0.00, 0.00, 0.00

```
Some commands take a switch or a flag to modify the command.  -n with echo does not print a new line.
```
$ echo -n 'Hello World'
Hello World[pslucas@ns02 ~]$
```

A command might looks like
```
$ <command> <options> <arguments>
```

Commands are categorized as two types: internal or built in commands (about 35) and external commands that rely on binary progams or scripts which are located in files.  Some external commands are installed with the systems and others are installed by the enduser.

'cd' - change direcotry is an example of a built in command

Internal command examples | What it does
-----------------|-------------
cd | change directory
mkdir | make a directory
pwd | print working directory


'type' command is used determine if the command is internal built-in command or an external command
```
$ type echo
echo is a shell buit-in
$ type mv
mv is hashed (/bin/mv)
```
### Basic Linux commands
Type (Present/Print Working Directory) 'pwd' to see the current directory
```
$ pwd
/home/<some user>
```

Run 'ls' the list command to see contents of the directory
```
$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```
Use mkdir the make directory command to make a diretory
```
$ mkdir someDir
```
You can create multiple directories at once.
```
$ mkdir Asia Europe Africa Ameria
```
You can create parent and children directories at the same time.  Use a '-p' switch with mkdir to make a new dir weith a child directory.
```
$ mkdir -p anotherDir/childDir 
```
To move a up one directory type 'cd ..'
```
$ cd ..
```
To return to your home directory, type 'cd ~'
```
[pslucas@ns02 /]$ cd ~
[pslucas@ns02 ~]$ 
```
Also can use cd with no arguments to retrun the home direcotry.    

Absolute path is a path that starts from the root directory
```
$ ls /home/pslucas/someDir/
```
Relative path is 'relative' to the current path
```
$ pwd
/home/pslucas
$ ls someDir/
childDir
```

You can also use the 'pushd' command to change a directory.  And then se the 'popd' command to go back to the starting directory that you changed to with the pushd
```
[pslucas@ns02 /]$ pushd /home/pslucas/
~ /
[pslucas@ns02 ~]$ cd someDir/
[pslucas@ns02 someDir]$ cd childDir/
[pslucas@ns02 childDir]$ popd
/
[pslucas@ns02 /]$ 
```

To move a file or directory use the 'mv' move command.  Used two arguements with the mv command: source and target directories
```
$ mv <source directory> <target directory>
```
You move files and directories with either absolute or relative paths
```
$ mv textToMove.txt someDir/childDir/
```
We can use the 'mv' file to rename files or direcories
```
$ mv paulfile.txt bobfile.txt
```

Use the 'cp' command to copy files.  The cp command expects two arguements: source and target
```
$ cp /home/bob/bobfilet.txt '/home/paul/'
```

Remove a file or directory with 'rm' remove command.  Note be careful with 'rm -r' as removes through the directory and below recursviley.

Also you can use -r to recursevily do other activities.  For example use 'cp -r' recuresively copy files

You can read the contents of file with the 'cat' command (concatenate).
```
$ cat bobfile.txt
```

To create a file with content type...
```
$ cat > newfile.txt
Type something here
Type more text here, and when you are finished adding test to the file, type Ctrl-d to write this file out.
```

To create an empty file use the 'touch' command
```
$ touch hello.txt
```

Pagers like 'more' or 'less' allow you to scroll through a file and are more efficient then the cat command.  The more and less command lets you scroll and search the test.

The 'more' command loads the entire file at once.  And this may be slow if the file is large

more Command | Result
--------------|-------
Space Bar | Scrolls text one display at a time
Enter key | Scrolls one line at a time
b key | Scrolls backwards one screen at a time
/ key | Search for text in the file
q key | Quits more

less Command | Result
--------------|-------
Up Arrow | Scrolls up one line at a time
Down Arrow | | Scrolls down one line at a time
Space Bar | Scrolls text one display at a time
Enter key | Scrolls one line at a time
b key | Scrolls backwards one screen at a time
/ key | Search for text in the file
q key | Quits more

Use the 'ls' command to list directoy.  Use 'ls -l' long list option to list additonal information like access mode, ownership, last access time, etc'
```
$ ls -l
total 0
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Desktop
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Documents
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Downloads
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Music
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Pictures
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Public
drwxrwxr-x. 3 pslucas pslucas 22 May  4 08:21 someDir
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Templates
-rw-rw-r--. 1 pslucas pslucas  0 May  4 08:23 textToMove.txt
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Videos
```

Use the -a option to get hidden directory and file information.
```
$ ls -a
.              .bashrc    Downloads      Music     .ssh
..             .cache     .esd_auth      Pictures  Templates
.bash_history  .config    .ICEauthority  .pki      textToMove.txt
.bash_logout   Desktop    .local         Public    Videos
.bash_profile  Documents  .mozilla       someDir   .viminfo
```
Add the -al option for a long list with hidden directories and filess
```
$ ls -al
total 32
drwx------. 17 pslucas pslucas 4096 May  4 08:28 .
drwxr-xr-x.  4 root    root      36 Mar 23 14:36 ..
-rw-------.  1 pslucas pslucas 2511 Apr 28 15:46 .bash_history
-rw-r--r--.  1 pslucas pslucas   18 Jul 26  2021 .bash_logout
-rw-r--r--.  1 pslucas pslucas  141 Jul 26  2021 .bash_profile
-rw-r--r--.  1 pslucas pslucas  376 Jul 26  2021 .bashrc
drwxr-xr-x. 11 pslucas pslucas  250 Apr 27 14:35 .cache
drwx------. 11 pslucas pslucas  215 Mar 23 14:07 .config
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Desktop
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Documents
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Downloads
-rw-------.  1 pslucas pslucas   16 Mar 17 10:47 .esd_auth
-rw-------.  1 pslucas pslucas  632 Mar 23 14:07 .ICEauthority
drwx------.  3 pslucas pslucas   19 Mar 21 15:17 .local
drwxr-xr-x.  4 pslucas pslucas   39 Mar 14 16:49 .mozilla
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Music
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Pictures
drwxrw----.  3 pslucas pslucas   19 Mar 21 15:17 .pki
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Public
drwxrwxr-x.  3 pslucas pslucas   22 May  4 08:21 someDir
drwx------.  2 pslucas pslucas   25 Apr  4 13:21 .ssh
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Templates
-rw-rw-r--.  1 pslucas pslucas    0 May  4 08:23 textToMove.txt
drwxr-xr-x.  2 pslucas pslucas    6 Mar 21 15:17 Videos
-rw-------.  1 pslucas pslucas  902 Mar 18 16:52 .viminfo
```

To see files in the order the files were modified.
```
$ ls -lt
total 0
-rw-rw-r--. 1 pslucas pslucas  0 May  4 08:23 textToMove.txt
drwxrwxr-x. 3 pslucas pslucas 22 May  4 08:21 someDir
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Desktop
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Documents
...
```
To see files modified in reverse order date...
``` 
$ ls -ltr
total 0
...
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Desktop
drwxrwxr-x. 3 pslucas pslucas 22 May  4 08:21 someDir
-rw-rw-r--. 1 pslucas pslucas  0 May  4 08:23 textToMove.txt
```
### Command Line Help
The 'whatis' command provides a one line descprtion of a command.  Note: there may not be informatin to display all linux distros
Example from Raspbian GNU/Linux 10 (buster)
```
$ whatis date
date (1)             - print or set the system date and time
```
Example from RHEL 8.x:
```
$ whatis date
date: nothing appropriate.
```
Use man (manual) pages to get a detailed description of a command along with usage examples.  Note: Type 'q' to quit out of man pages.
```
$ man date
DATE(1)                          User Commands                         DATE(1)

NAME
       date - print or set the system date and time

SYNOPSIS
       date [OPTION]... [+FORMAT]
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

DESCRIPTION
       Display the current time in the given FORMAT, or set the system date.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.
...
```
You can use the following 'more' commands to navigate through a man page
more Command | Result
--------------|-------
Space Bar | Scrolls text one display at a time
Enter key | Scrolls one line at a time
b key | Scrolls backwards one screen at a time
/ key | Search for text in the file
q key | Quits more

Most commands have buit-in help use the '--help' option with the command
```
$ date --help
Usage: date [OPTION]... [+FORMAT]
  or:  date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
Display the current time in the given FORMAT, or set the system date.
...
```

Use 'apropos' along with the command as the argument to find all man page with references to the command
An Example From Debian..
```
$ apropos date
arm-linux-gnueabihf-elfedit (1) - Update the ELF header of ELF files.
asctime (3)          - transform date and time to broken-down time or ASCII
asctime_r (3)        - transform date and time to broken-down time or ASCII
cal (1)              - displays a calendar and the date of Easter
catman (8)           - create or update the pre-formatted manual pages
...
```
An Example from RHEL 8
```
$ apropos date
date: nothing appropriate.
```
### Lab Example
What's the home director for bob:
```
$ pwd
/home/bob
```
or use echo $HOME to find the home directory
```
$ echo $HOME
/home/bob
```

What type of command is git?
```
$ type git
git is /usr/bin/git
```
Make a directory called birds
```
$ mkdir birds
```
Make directoires /fish/salmon in one command
```
$ mkdir -p fish/salmon
```
Make additional directories
```
$ mkdir -p mammals/elephant mammals/monkey birds/eagle reptile/snake reptile/frog amphibian/salamander 
```
Move directory frog from reptile to amphiban
```
$ mv reptile/frog/ amphibian/
```
Rename directory snake to crocodile
```
$ mv reptile/snake reptile/crocodile
```
Remove reptile
```
rm -r reptile/
```
 

### Linux Shells
Shell types in Linux
- Bourne Shell (sh) developed in 70s for Unix
- C Shell (csh or tcsh)
- Korn Shell (ksh)
- Z shell (zsh)
- Bourne again Shell (bash)

All shells facilate the interaction between the user and the operating system.   
To check the shell in use type 'echo $SHELL'
```
$ echo $SHELL
### Shell Commands
/bin/bash
```
Use 'chsh' to change the shell. Note: you need to run this command with super user (root) privelages on RHEL 8.  Debian allows the user to change the shell after supplying their password.
```
$ sudo chsh
Password: 
Changing the login shell for pslucas
Enter the new value, or press ENTER for the default
	Login Shell [/bin/bash]:
```
***Note:*** In the KodeKloud I had to use the following command to change shell
```
$ sudo chsh -s /bin/sh bob
```

### BASH Features
The bash shell supports autocomplete of commands, directories and file names. Use the tab key for autocompleteion.      
In the bash shell we can set short cuts with 'alias' command
```
$ alias dt=date
$ dt
Tue 26 Apr 2022 10:45:18 AM CDT
```
The 'history' command shows the history of the command you used previously
```
$ history
  661  top
  662  top help
  663  ps -ef
  664  clear
  665  top
  666  w
  667  ptree
```

Environent variables $XXXXX are named and can be seen with a $echo <environment name>.  Variables are used to store information like shell type, home dir, search path, etc.

Show environment settings.  Example from debian..
```
$ env
SHELL=/bin/bash
LANGUAGE=en_US.UTF-8
NO_AT_BRIDGE=1
PWD=/home/pslucas
LOGNAME=pslucas
XDG_SESSION_TYPE=tty
HOME=/home/pslucas
LANG=en_US.UTF-8
...
```
Set environment variable wwith the export command
```
$ export NAME=paul
$ echo $NAME
paul
```
Show path
```
$ echo $PATH
```
Add to Path to path environment variable
```
$ export $PATH:/somedir
```
The path environment variable provides a list of directories to searh in for a command.  If the a driectory is not liseted in the the path, command will not execute or be found.  You can the 'which' command to find the location of a command.
```
$ which obs-studio
obs-studion: command not found
```
Add path for obs-studion application
```
$ export PATH=$PATH:/opt/obs/bin
$ which obs-studio
/opt/obs/bin/obs-studio
```
	
Show shell prompt set at login time.
```
$ echo $PS1
[\u@\h \W]\$
```

### Customize the bash prompt    
Prompt shows information like path and user
```
[pslucas@ns02 ~]$
```
What the shell prompt means... '~ = present working directory and '$ = user prompt symbol'
Change prompt example - Add date between brackets, then username @ hostname working directory : $ -> [Wed Sep 15]bob@caleston-lp10:~$   
PS1 is the most common varialbe used to creat the user prompt.
```
$ PS1='[\d]\u@\h:\w$'
```
Make it permanent in ~/.profile
```
echo 'PS1="[\d]\u@\h:\w$"' >> ~/.profile
```
or add the following to .profile
```
PS1="[\d]\u@\h:\w$"
```
To make environment variables persistent add them to the '~/.profile (debian) or ~/.pam_enviroment' or ~/.bash_profile (Red Hat) file.

Check if location can be found for a program.  If it can't be found, add to the path.
```
$ which cd
/usr/bin/cd
```
### Lab Example: Linux bash prompt
What is bob's default shell?
```
$ echo $SHELL
/bin/bash
```
Change bob's shell to the bourne shell
```
$ sudo chsh -s /bin/sh bob
```
or ...
```
$ sudo chsh
[sudo] password for bob: 
Changing the login shell for root
Enter the new value, or press ENTER for the default
        Login Shell [/bin/bash]: /bin/sh
```
What's the value of the variable TERM
```
$ echo $TERM
xterm-256color
```
Make a new environment varialbe PROJECT=MERCURY and persist to the ~/.profile file
```
$ export PROJECT=MERCURY
$ echo $PROJECT
MERCURY
$ echo PROJECT=MERCURY >> ~/.profile
```
Make an alias up for uptime and persist the change to the ~/.profile file
```
$ alias up=uptime
$ up
 21:13:05 up 16 min,  0 users,  load average: 4.47, 5.59, 5.36
$ echo alias up=uptime >> ~/.profile 
```
