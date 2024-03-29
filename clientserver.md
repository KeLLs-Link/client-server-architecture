### Client-Server-Architecture Implementation:

![image](./screenshot/clientserverarchitecture.png)
- **This project is deployed on AWS Cloud**

Let's Begin 👍

Privission two Linux-based virtual servers (EC2 instances in AWS).

```
Server A name - `mysql server``

Server B name - `mysql client`
```
![screenshot](./screenshot/serverandclient.png)


On `mysql server` , install MySQL Server software.
```
sudo apt install mysql-server
```
Start mysql server
```
sudo systemctl start mysql.service
```
Ensure that the server is running using the systemctl command:
```
sudo systemctl status mysql.service
```
![image](./screenshot/mysqlserver.png)

![screenshot](./screenshot/statusrunning.png)

Verify that `mysql-client and server` are installed

```
dpkg -l | grep mysql-client
dpkg -l | grep mysql-server
```
The above comands are for Debian-based distributions like Ubuntu.

If you're using a different package management system or distribution, such as CentOS or Fedora, you may need to use different command as shown below.

```
rpm -qa | grep mysql-server
rpm -qa | grep mysql-client
```

![screenhot](./screenshot/mysqlclientverified.png)


![screenshot](./screenshot/mysqlserverconfirmed.png)


 - ## **Configure mysql server**

```
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
```
Run a MySQL secure installation
```
sudo mysql_secure_installation
```
![image](./screenshot/mysqldbconfigured.png)

In the `MySQL server`, create a user and a database named first_db and a user named first_user, but you can replace these names with different values.

First, connect to the MySQL console using the root account
```
sudo mysql -p
```

Create a new database by running this command in your MySQL console:
```
CREATE DATABASE example_database;
```

Create a new user and grant full privileges on the database we have just created.
```
CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'PassWord';
```

N/B: The following command above creates a new user named `example_user`, using mysql_native_password as default authentication method. We’re defining this user’s password as password, but you should replace this value with a secure password of your own choosing.

Give this user permission over the example_database database:
```
GRANT ALL ON example_database.* TO 'example_user'@'%';
```

![image](./screenshot/configuredmysqluser.png)

exit mysql console with the following command:
```
exit
or type
\q
```
bye 😄

***Note: This will give the example_user user full privileges over the example_database database, while preventing this user from creating or modifying other databases on your server.***

Test if the new user has the proper permissions by logging in to the MySQL console again, this time using the custom user credentials:
```
mysql -u example_user -p
```
confirm access to the database

```
SHOW DATABASES;
```
![image](./screenshot/configfinished.png)

The `-p` flag in the command above prompts you to input the password you used when creating the example_user. 

Restart your mysql server and ensure its running.
```
sudo systemctl restart mysql
sudo systemctl status mysql.service
```

**`MySQL server`** uses TCP port `3306` as it's default port so you will have to open this port by allowing an Inbound rule in your security group.

![image](./screenshot/mysql-server-port.png)

Configure MySQL server to allow connections from remote hosts

```
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
You can open the above command using your favourite command line editor.

Replace the bind address

```
127.0.0.1 
```
![image](./screenshot/bindadress.png)
with
```
0.0.0.0
```
![image](./screenshot/bindaddressedited.png)

save and exit your command line code editor.

From `mysql client` Linux Server, connect remotely to mysql server Database Engine without using SSH. You must use the `mysql utility` to perform this action.

use the command below to onnect remotely to `mysql-server` from `mysql-client` machine and perform sql queries.

N/B: replace the Ip address with the Privte ip address of your server.
```
sudo mysql -u example_user -h 172.31.6.225 -p
```

type the ***show databases;*** command and the example database should be available.
```
show databases;
```

![image](./screenshot/completed.png)

Congratulations 👍

- Clean up

Do not forget to stop or terminate your EC2 Instances (Client and Server machines) in order not to incure charges.

