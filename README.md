# KodeKloud Linux Basics: Working with the Shell Part 1

[KodeKloud Linux Basics Course Notes Table of Contents](https://github.com/pslucas0212/LinuxBasics)


### Linux Command line
The Linux shell is a prorgam interface between the user and computer.  When you login you are taken to a computer generated directory known as the home directory.  This is users home folder or directory which is located under /home:
```
/home/<user name>
```
On the commnand lin promte, the home directory is denoted by a ~ symbol.  The ~ represents the home directory
```
[pslucas@ns02 ~]$
```

- On the command line you enter a command like the "echo" command.  Commands take arguements.  The echo command takes a string text as an argument
```
$ echo 'Hello World'
Hello World
```
- Some commands do not need an argument like the "uptime" command which shows how long the system has been running
```
$ uptime
 08:12:02 up 33 days, 18:46,  1 user,  load average: 0.00, 0.00, 0.00

```
- Some commands take a switch or a flag to modify the command
```
$ echo -n 'Hello World'
Hello World[pslucas@ns02 ~]$
```

So a command might look likce
```
$ <command> <argument> -<option>
```

- Commands are categorized as two types: internal or build in commands (about 35) and external commands that rely on binary progams or scripts which are located in files.  Some come installed with the systems and others are installed by the enduser.

- 'cd' - change direcotry is an example of a built in command

Internal command examples | What it does
-----------------|-------------
cd | change directory
mkdir | make a directory
pwd | print working directory


- 'type' command to determine if the command is internal built-in or external
```
$ type echo
echo is a shell buit-in
$ type mv
mv is hashed (/bin/mv)
```
### Basic Linux commands
- TYpe (Print Working Directory) 'pwd' to see the current directory
```
$ pwd
/home/<some user>
```

- run 'ls' - list command to see contents of the directory
```
$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```
- mkdir (makes a directory).
```
$ mkdir someDir
```
- You can create parent and children directories at the same time.  Use a '-p' switch with mkdir to make a new dir weith a child directory.
```
$ mkdir anotherDir/childDir -p
```
- To move a up a directory type 'cd ..'
```
$ cd ..
```
- To return to your home directory, type 'cd ~'
```
[pslucas@ns02 /]$ cd ~
[pslucas@ns02 ~]$ 
```

- Absolute path is a path that starts from the root directory
```
$ ls /home/pslucas/someDir/
```
- Relative path is 'relative' to the current path
```
$ ls someDir
```

- you can also use the 'pushd' command to change a directory
- Use the 'popd' command to go back to the starting directory
```
[pslucas@ns02 /]$ pushd /home/pslucas/
~ /
[pslucas@ns02 ~]$ cd someDir/
[pslucas@ns02 someDir]$ cd childDir/
[pslucas@ns02 childDir]$ popd
/
[pslucas@ns02 /]$ 
```

- To move a file or directory use the 'mv' move command.  Used two arguements with the mv command: source and target directories
```
$ mv <source directory> <target directory>
```
- You move files and directories with either absolute or relative paths
```
$ mv textToMove.txt someDir/childDir/
```
- We can use the 'mv' file to rename files or direcories
```
$ mv paulfile.txt to bobfile.txt
```

- Use the 'cp' command to copy files
```
$ cp /home/bob/bobfilet.txt '/home/paul/'
```

- Remove a file or directory with 'rm' remove command.  Note be careful with 'rm -r' as removes through the directory and below recursviley.

- Also you can use -r to recurseviley do other activities.  For example use 'cp -r' recuresively copy files

- You can read the contents of file with the 'cat' command (concatenate).
```
$ cat bobfile.txt
```

- To create a file with content type...
```
$ cat > newfile.txt
Type something here
Type more text here, and when you are finished adding test to the file, type Ctrl-d to write this file out.
```

- To create an empty file use the 'touch' command
```
$ touch hello.txt
```

- Pagers like 'more' or 'less' allow you to scroll through a file and are more efficient then the cat command

- more loads the entire file at one time.  And this may be slow if the file is large

more commands | result
--------------|-------
Space Bar | Scrolls text one display at a time
Enger key | Scrolls one line at a time
b key | Scrolls backwards one screen at a time
/ key | Search for text in the file
q key | Quits more

- Use the 'ls' command to list directoy.  Use 'ls -l' long list option to list additonal information like access mode, ownership, last access time, etc'
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

- Use -a to get hidden directory and file information.
```
$ ls -a
.              .bashrc    Downloads      Music     .ssh
..             .cache     .esd_auth      Pictures  Templates
.bash_history  .config    .ICEauthority  .pki      textToMove.txt
.bash_logout   Desktop    .local         Public    Videos
.bash_profile  Documents  .mozilla       someDir   .viminfo
```
Add the -l swithc for a long list with hidden directories and filess
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

- To see fils in order of creation date
```
$ ls -lt
total 0
-rw-rw-r--. 1 pslucas pslucas  0 May  4 08:23 textToMove.txt
drwxrwxr-x. 3 pslucas pslucas 22 May  4 08:21 someDir
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Desktop
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Documents
...
```
- To see files create in reverse order date...
``` 
$ ls -ltr
total 0
...
drwxr-xr-x. 2 pslucas pslucas  6 Mar 21 15:17 Desktop
drwxrwxr-x. 3 pslucas pslucas 22 May  4 08:21 someDir
-rw-rw-r--. 1 pslucas pslucas  0 May  4 08:23 textToMove.txt
```
### Command Line Help
 - The 'whatis' command provides a one line descprtion of a command.  Note: there may not be informatin to display all linux distros
 - Example from Raspbian GNU/Linux 10 (buster)
```
$ whatis date
date (1)             - print or set the system date and time
```
- Example from RHEL 8.x:
```
$ whatis date
date: nothing appropriate.
```
- Use man (manual) pages to get a detailed description of a command along with usage examples.  Note: Type 'q' to quit out of man pages.
```
$ mand date
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
- Most commands have buit-in help use the '--help' option with the command
```
$ date --help
```
- Use 'apropos' along with the command as the argument to find all man page with references to the command
```
$ apropos date
```
### Linux Shells
- Bourne Shell (sh) developed in 70s for uniux
- C Shell (csh or tcsh)
- Korn Shell (ksh)
- Z shell (zsh)
- Bourn again Shell (bash)
- All shells facilate the interaction between the user and the operating system.
- To check the shell in use type 'echo $SHELL'
```
$ echo $SHELL
### Shell Commands
/bin/bash
```
- Use 'chsh' to change the shell.  
```
$ chsh
Password: 
Changing the login shell for pslucas
Enter the new value, or press ENTER for the default
	Login Shell [/bin/bash]:
```

### BASH Features
- bash will complete commands and directories with auto complietion
- We can set short cuts with 'alias' command
```
$ alias dt=date
$ dt
Tue 26 Apr 2022 10:45:18 AM CDT
```
- The 'history' command shows the history of the command you used previously

- Environent variables $XXXXX

- Show environment settings
```
$ env
```
- Set environment variable
```
$ export NAME=paul
```
- Add to Path to path environment variable
```
$ export $PATH:/somedir
```
- Show default shell
```
$ echo $SHELL
```
- Show prompt settings
```
$ echo $PS1
```
- Change shell
```
$ sudo chsh -s /bin/sh <username>

```
- Show path
```
$ echo $PATH
```
- Check if location can be found for a program.  If it can't be found, add to the path.
```
$ which obs-studio
```

- Create alias
```
$ alias up=uptime
```
- Prompt shows information like path and user
```
[~]$
```
-  '~ = present working directory" and '$ = user prompt symbol'
- Change prompt example - Add date between brackets, then username @ hostname working directory : $ -> [Wed Sep 15]bob@caleston-lp10:~$
```
$ PS1='[\d]\u@\h:\w$'
```
- Make it permanent in ~/.profile
```
echo 'PS1="[\d]\u@\h:\w$"' >> ~/.profile
```

- To make environment variables persistent add them to the '~/.profile or ~/.pam_enviroment' file.
