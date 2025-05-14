## 🐧 Linux Beginer to Advanced (in one shot)

Welcome to your first steps into the Linux world! This repository includes:

- 📦 Installation steps (Ubuntu/CentOS)
- 🧭 Basic command-line navigation
- 🔐 File permissions and ownership
- 📂 File system structure
- 📜 Intro to shell scripting

> Start here if you're completely new to Linux.


## Super user (admin) : 

To switch back to root user(admin) on AWS linux:  

- `sudo -i` (AWS)  
- `sudo su` (AWS)  
  Ec2-user does not have enough privilege so we need to make it root user by `sudo -i` or `sudo su` (super user do switch user - make me root user)  
- `su root` (Alma/ aws with root password)

> 💡 **Note:** All three commands provide root-level access and privileges, but `sudo -i` is best for fully getting the root’s environment and `su root` has to provide the root password.

## User and information: 

- To check the current user  
  `whoami`

- To create user  
  `useradd Anas` or `adduser Anas`

- To give the user (Anas) the password (as root user)  
  `passwd Anas`

- To rename user name:  
  `usermod -l mYnewUser oldAnasUser`  
  *(warning: do with caution and also if has running process it won't execute so we need to kill the process `pkill -u oldAnasUser`)*

- To check user id & group  
  `id Anas`

- To substitute user or become different user (operate as diff user):  
  `su newUser`  
  Example: `su Anas`

- To check all users or user list:  
  `cat /etc/passwd`  
  `getent passwd | cut -d: -f1`  
  *(it will only show the users)*

- Check specific user:  
  `getent passwd Anas`  
  *(give the user name here)*

- To delete a user:  
  `userdel Anas`

- To lockout a user:  
  `usermod -L Anas`  
  *(it makes the password invalid)*  
  `passwd -l Anas`  
  *(It locks the account by specifically altering the password field)*

- To unlock a user:  
  `usermod -U Anas`

- Force the user to change the password:  
  `chage -d 0 Anas`

- To setup the expiration of user account:  
  `chage -E 2025-01-01 Anas`  
  `usermod -e 2024-12-31 Anas`

- To remove user expiration:  
  `chage -E -1 Anas`

- To check when is the expiration for a user:  
  `chage -l Anas`

- To check who(user) is currently log in:  
  `who`

## User group & permission: 

- To create group:  
  `groupadd DevOpsTeam`

- To check the group:  
  `getent group`  
  `cat /etc/group`

- To find which group the user Anas belongs to:  
  `grep anas /etc/group`

- To add someone to a group:  
  `usermod -aG DevOpsTeam Anas` *(include the group then the user)*

- To remove someone from a group called DevOpsTeam:  
  `gpasswd -d Anas DevOpsTeam` *(include the user then the group)*

- To add multiple groups for a file:  
  `usermod -aG DevOpsTeam Anas` *(for the first group)*  
  `setfacl -m g:qa:rwx Anas.txt` *(for the 2nd group)*

- To check a specific group by name:  
  `getent group DevOpsTeam`

- To delete a group:  
  `groupdel DevOpsTeam`

- Check who belongs to the current group:  
  `getent group DevOpsTeam` *(include the group name: DevOpsTeam)*

- To check the group of a user:  
  `id alice`

- To check the file list and folder permission:  
  `ls -ld` *(show the permission, showing long detail, list information about the directory only, current folder)*  
  `ls -all` *(show all file permission and details)*  
  `ls -ld file1.txt` *(finding a specific file permission)*  
  `ls -ll` *(show non-hidden files and folders within current directory)*  
  `ls -l filename.txt` *(show permission list)*  
  `ll` *(works like `ls` but gives list of their permission and users' information as well)*

- To change the current owner of a file or folder:  
  `chown mike devOpsFile.txt`  
  `chown -R username DirName` *(flag is used for recursive changes, applying the group change to all files and directories within a specified directory)*

- To allow a group (DevOpsTeam) to have all (RWX) permissions for a file only:  

  Step 1: Change the file ownership (group):  
  `chown :DevOpsTeam DevOpsFile` *(include the group name then filename)*  
  `chgrp -R groupName DirectoryName` *(flag is used for recursive changes, applying the group change to all files and directories within a specified directory)*  

  Step 2: By default, the group should have read permission, so now to add write and execute:  
  `chmod g+wx DevOpsFile` *(add the file name at the end)*  
  *(Note: It has given the group full privilege)*

  Step 3: Login a user that is part of DevOpsTeam to see if it got the permission.

- Allow only read and write permission for group for DevOpsFile:  
  `chmod g=rw DevOpsFile`

- Allow also write permission for group:  
  `chmod g+w DevOpsFile`

- Allow only read permission for group:  
  `chmod g=r DevOpsFile`

- Allow owner to only have read permission:  
  `chmod u=r DevOpsFile`

- Allow owner to have rwx permission:  
  `chmod u=rwx DevOpsFile`

- Allow others not to read anything:  
  `chmod o= DevOpsFile`

- Not to allow any permission for the group:  
  `chmod g= DevOpsFile` *(Note: We are not providing any value to `g`, so this changes why the group has no permission to read, write, or execute)*  
  *(It will show 3 dashes (- - -), which means it got no permission to any of them (RWX))*

- Allow everyone rwx:  
  `chmod 777 DevOpsFile`

- Not allow RWX for everyone:  
  `chmod 000 DevOpsFile`

- Not allow anyone to delete the file except the owner:  
  `chmod +t fileName`

- To remove sticky bit:  
  `chmod -t fileName`


## Folder and Navigation: 

  - To check folder in tree structure:  
    `tree`

  - To go to the root folder will take you to the root:  
    `cd /`

  - To go the folder called tmp:  
    `cd /tmp`

  - To go to the home folder:  
    `cd ~`

  - To check files and folders:  
    `ls`

  - To show the long list:  
    `ls -ll`

  - To show all the files:  
    `ls -al`

  - To display information about the directory itself:  
    `ls -ld`

  - To create a folder or directory:  
    `mkdir myFolder`  
    Ex: `mkdir AnasFolder`

  - To drop or delete an empty folder:  
    `rmdir foldername`  
    Ex: `rmdir AnasFolder`

  - To drop folder forcefully:  
    `rm -rf docker_practice_folder`

  - To make nested folders:  
    `mkdir -p firstFolder/secondFolder/thirdFolder`  
    *(Note: `-p` creates parent directories as needed. If the folder already exists, give the folder name as parent, e.g., `mkdir existingFolder/secondFolder`.)*

  - To drop file or folder with content:  
    `rm -r foldername`  
    `rm -r helloWorld`  
    *(This will ask permission to delete the file or folder.)*  
    `rm -rf helloWorld`  
    *(The `-rf` flag allows you to forcefully delete the folder with content inside without asking any questions.)*

  - To delete everything from a directory:  
    `rm -rf *`

  - To delete every file that has the letter F in them:  
    `rm -rf *F*`

  - To rename a folder’s name:  
    `mv oldname newgivenName`

  - To go to folder called Anas:  
    `cd /home/Anas`

  - To check the present working directory:  
    `pwd`

  - To go back to previous folder:  
    `cd ..`  
    Ex: `cd ..`

  - To go back 6 steps back:  
    `cd ../../../../../../`

  - To move to the next folder:  
    `cd */`  
    *(Note: This only works when the next folder has only one folder.)*

  - To check the current folder size:  
    `df -h`


## Notifications:

  - To notify everyone:  
    `wall “hello everyone, please turn off your pc now, we will do work on server”`

  - To display on green:  
    `echo “hello world”`

## Software Installation:

  - To download and install something:  
    `wget provideTheDownloadableURLhere`

  - Check recent package or software installation history:  
    `dnf history`

  - To check if a package called tree is installed or not:  
    `rpm -q tree`

  - To check if nano is installed:  
    `which nano`

  - To install firewall:  
    `yum install firewalld`

  - To activate firewall:  
    `systemctl start firewalld`

## Machine Information:

  - To check hostname/device name:  
    `hostname`

  - To check IP address:  
    `ip addr`  
    `ohai ipaddress`

  - To check hostname, OS:  
    `uname -a`

  - To change the hostname/computer name (root user):  
    `hostnamectl set-hostname pitt`

  
## Handy Tools:

  - To clear your screen:  
    `clear`

  - To check the history of Linux commands:  
    `history`

  - To interrupt the command/To get back to the command if you typed `cd` instead of `cd ~`:  
    `Ctrl + C`

  - To go back to previous state like `Ctrl + Z` on Nano:  
    `Alt + E`

## To Create, Read & Write Files:

  - To create a file:  
    `touch fileAnas.txt`

  - To create a single file:  
    `touch file1.txt`

  - To create 10 files:  
    `touch testfile{1..10}.txt`

  - (Nano) To write on a file, use Nano, which is a text editor for Linux:  
    `nano fileAnas.txt`  
    After writing, press `CTRL + O` to save, then press `Enter`  
    To get out of Nano, press `CTRL + X`

  - To create a new file through Nano:  
    `nano newfile.txt`

  - To go back to previous state like `Ctrl + Z` on Nano:  
    `Alt + E`

  - To read files:  
    `cat file1.txt`  
    Example:  
    `cat anasFile.txt`

  - With the `cat` command, you can also write to a file:  
    `cat >> newfile` (then add your text, it will create the new file called `newfile` and also add the text for the file once you press `Enter`)

  - To go to the root folder:  
    `/`

  - To go to home:  
    `cd ~`

  - To create a hidden file:  
    `touch .file1`  
    *(Note: If we add a dot before the file name, Linux hides the file by default)*

  - To check the hidden file:  
    `ls -a` *(This will list all files, including hidden ones)*

## To Copy, Cut, and Paste Files and Folders:

To copy a file and paste it in the same directory:  
`cp sourceFile DestinationFile`  
(Note: The `DestinationFile` will be newly created. If a file with the same name exists, it will ask to override.)  
Example:  
`cp file1 newFile`

To copy a file to a directory:  
`cp file1 dir1`

To copy a file to somewhere far (use full path):  
`cp file1 /home/ec2-user/dir1`  
(Note: We are in the current directory, and transferring the file to `dir1` in another location, so full path is needed.)

To copy everything from a folder to another:  
`cp -r sourcefolder/* destinationFolder`  
Example:  
`cp -r /home/ec2-user/folder1/* destinationFolder`

## To map folder to another folder:

To connect one folder to another using symlink:  
`ln -s /home/ubuntu/anas /tmp`

- To cut (move) a file:**

`mv file1 newFolder`  
(Note: The file and folder need to be in the same directory; otherwise, it will rename instead of cut.)

- To cut (move) or relocate a folder:

`mv folder everything`

- To append text from output to a file:

`ip addr >> file1`

- To replace text from output to a file:

`ip addr > file1`

**Search and Findings:**

To check if there is a file named `myfile.txt`:  
`ls myfile.txt` *(from the current folder)*  
`find /home/green/myDir -name myfile.txt` *(if you know the directory)*  
`find . -name "myfile.txt"` *(from current folder)*  
`find -name myfile.txt`  
(This will show all the files with the same name from all directories. Note: This needs to be executed from the root directory.)

To find a specific text like "hello world" from all files within the `/home` directory:  
`grep -r "hello world" /home`  
`grep -ri "hello world" /home` *(ignore case sensitivity)*

To check which files have been modified in the last 2 days:  
`find /tmp -mtime -2`

To search for anything that starts with `a` and ends with `.txt`:  
`find / -name a*.txt`

To find a file that is larger than 100MB:  
`find / -size +100M`

To check the type of a file:  
`file /etc/passwd`

To find any username "ec2":  
`grep -ri "ec2*" /etc/passwd`

**To Replace Word or Text in a File:**

To replace `ramim123` text with `***`:  
`sed -i 's/ramim123/***/g' helloworld.txt`  
(This will insert `***` globally in place of `ramim123` in `helloworld.txt`.)

To display a mask as `**` on display:  
`sed 's/ramim123/***/g' hello`

    
