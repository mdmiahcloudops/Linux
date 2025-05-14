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
  (warning: do with caution and also if has running process it won't execute so we need to kill the process `pkill -u oldAnasUser`)
  
- To check user id & group  
  `id Anas`
  
- To substitute user or become different user (operate as diff user):  
  `su newUser`  
  Ex. `su Anas`
  
- To check all users or user list:  
  `cat /etc/passwd`  
  `getent passwd | cut -d: -f1`  
  (it will only show the users)
  
- Check specific user:  
  `getent passwd Anas`  
  (give the user name here)
  
- To delete a user:  
  `userdel Anas`
  
- To lockout a user:  
  `usermod -L Anas`  
  (it makes the password invalid)  
  `passwd -l Anas`  
  (It locks the account by specifically altering the password field)
  
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



