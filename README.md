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

<ul>
  <li><strong>To check the current user</strong>: <span style="color:green">whoami</span></li>
  <li><strong>To create user</strong>: <span style="color:green">useradd Anas</span> or <span style="color:green">adduser Anas</span></li>
  <li><strong>To give the user (Anas) the password (as root user)</strong>: <span style="color:green">passwd Anas</span></li>
  <li><strong>To rename user name:</strong> <span style="color:green">usermod -l mYnewUser oldAnasUser</span> 
    <br> <em>(warning: do with caution and also if has running process it won't execute so we need to kill the process <span style="color:green">pkill -u oldAnasUser</span>)</em>
  </li>
  <li><strong>To check user id & group</strong>: <span style="color:green">id Anas</span></li>
  <li><strong>To substitute user or become different user (operate as diff user):</strong> <span style="color:green">su newUser</span>
    <br> <em>Ex. <span style="color:green">su Anas</span></em>
  </li>
  <li><strong>To check all users or user list:</strong> 
    <br> <span style="color:green">cat /etc/passwd</span>
    <br> <span style="color:green">getent passwd | cut -d: -f1</span> 
    <br> <em>(it will only show the users)</em>
  </li>
  <li><strong>Check specific user:</strong> <span style="color:green">getent passwd Anas</span>
    <br> <em>(give the user name here)</em>
  </li>
  <li><strong>To delete a user:</strong> <span style="color:green">userdel Anas</span></li>
  <li><strong>To lockout a user:</strong>
    <br> <span style="color:green">usermod -L Anas</span> <em>(it makes the password invalid)</em>
    <br> <span style="color:green">passwd -l Anas</span> <em>(It locks the account by specifically altering the password field)</em>
  </li>
  <li><strong>To unlock a user:</strong> <span style="color:green">usermod -U Anas</span></li>
  <li><strong>Force the user to change the password:</strong> <span style="color:green">chage -d 0 Anas</span></li>
  <li><strong>To setup the expiration of user account:</strong>
    <br> <span style="color:green">chage -E 2025-01-01 Anas</span>
    <br> <span style="color:green">usermod -e 2024-12-31 Anas</span>
  </li>
  <li><strong>To remove user expiration:</strong> <span style="color:green">chage -E -1 Anas</span></li>
  <li><strong>To check when is the expiration for a user:</strong> <span style="color:green">chage -l Anas</span></li>
  <li><strong>To check who(user) is currently log in:</strong> <span style="color:green">who</span></li>
</ul>



