# KodeKloud Linux Working with the Shell Part 1

[KodeKloud Linux Basics Course Notes Table of Contents](https://github.com/pslucas0212/LinuxBasics)


### Linux Command line
The inux shell is a prorgam interface between the user and computer.  When you login you are taken to computer generated directory known as the home directory.  Located under:
```
/home/<user name>
```
The home directory is denoted by a ~ symbol.  The ~ represents the home directory

- On the command line you enter a command like the "echo" command.  Commands take arguements.  The echo command takes a string text as an argument
```
$ echo 'Hello World!;
```
- Some commands do not need an argument like the "uptime" command which shows how long the system has been running
- Some commands take a switch or a flag to modify the command
```
$ echo -n 'Hello world'
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
- Run 'pwd' to see the current directory
```
$ pwd
/home/<some user>
```

- run 'ls' - list command to see contents of the directory
- mkdir (makes a directory).
- You can create parent and children directories at the same time

- To move a up a directory type 'cd ..'
- To return to your home directory, type 'cd ~'

- Absolute path is a path that starts from the root directory
- Relative path is 'relative' to the current path

- you can also use the 'pushd' command to change a directory
- Use the 'popd' command to go back to the starting directory

- To move a file or directory use the 'mv' move command.  Used two arguements with the mv command: source and target directories
```
$ mv <source directory> <target directory>
```
- You move files and directories with either absolute or relative paths
- We can use the 'mv' file to rename files or direcories
```
$ mv paulfile.txt to bobfile.txt
```

- Use the 'cp' command to copy files
```
$ cp /home/bob/bobvilet.txt '/home/paul/'
```

- Remove a file or directory with 'rm' remove command

- Use 'cp -r' recuresively copy files

- You can read the contents of file with the 'cat' of concatenate file
```
$ cat bobfile.txt
```

- To create a file with content type...
```
$ cat > newfile.txt
Type something here
Type more and with finished type Ctrl-d to write this file out.
```

- To create an empty file use the 'touch' command
```
$ touch hello.txt
```

- Pagers like 'more' or 'less' allow you to scroll through a file

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
```

- Use -a to get hidden directory information.
```
$ ls -a
$ ls -al
```

- To see fils in order of creation date
```
$ ls -lt
```
- To see files create in reverse order date...
``` 
$ ls -ltr
```
### Command Line Help
 - The 'whatis' command provides a one line descprtion of a command.
```
$ whatis date
```
- Use man (manual) pages to get a detailed description of a command along with usage examples.
```
$ man date
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
