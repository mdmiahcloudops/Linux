

# Setting up MySQL Server (AWS LINUX) 🐧💻

### To install MySQL on Linux (AWS) 🚀

Step 1: Run the following commands:  
`wget https://dev.mysql.com/get/mysql84-community-release-el9-1.noarch.rpm`

Step 2: Install the downloaded package  
`yum install mysql84-community-release-el9-1.noarch.rpm`

Step 3: Now install the MySQL server  
`yum install mysql-community-server`

Step 4: Start the MySQL service  
`systemctl start mysqld`

Step 5: Grep the temporary MySQL password  
`cat /var/log/mysqld.log | grep "password"`

Example:  
`Hv?fwrslV3Bn` 📝

Step 6: Login to MySQL  
Step 1: Type the following command to login  
`mysql -u root -p`

Step 2: Provide the temporary password:  
`Hv?fwrslV3Bn` 🔑

Step 3: Give a new password  
Step 1: Alter the root user password  
`ALTER USER 'root'@'localhost' IDENTIFIED BY 'S3cur@Passw0rd!';` 🔒

New password that I set is: `'S3cur@Passw0rd!'` ✨

🎉 **Congrats, database has been installed and configured!** 🎊
