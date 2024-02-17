# apache_on_ec2
Learn to install and configure Apache on an EC2 instance with two simple hosted pages serving as two web apps.

•	Apache configuration file edit

Steps:

1.	Run: sudo apt update
2.	Run: sudo apt install apache2
3.	Run: ls /
4.	Run: cd /etc/apache2/sites-available
5.	Run: ls
6.	Run: sudo vim 000-default.conf

7.	add following configurations and save the file
# for app 1
```
<VirtualHost *:5085>  
ServerName localhost ServerAlias
ServerAdmin webmaster@localhost 
DocumentRoot /var/www/html/app1 
ErrorLog ${APACHE_LOG_DIR}/error.log 
CustomLog ${APCHE_LOG_DIR}/access.log
</VirtualHost>
```

# for app 2
```
<VirtualHost *:8000>  
ServerName localhost ServerAlias
ServerAdmin webmaster@localhost 
DocumentRoot /var/www/html/app2 
ErrorLog ${APACHE_LOG_DIR}/error.log 
CustomLog ${APCHE_LOG_DIR}/access.log
</VirtualHost>
```
8.	Run: sudo vim /etc/apache2/ports.conf

9.	add following in the end of the file 

  	 "Listen 8000"    # for app 1

  	 "Listen 5085"    # for app 2

11.	Add two inbound rules in your instance’s security group to enable both ports (5085, 8000)

12.	Run: systemctl restart apache2

13.	Open the browser insert your instance public ip:port and press enter.
  
For example:
       ```
       http://43.204.216.0:5085
       ```
       ```
       http://43.204.216.0:8000
       ```  
