# WEB STACK IMPLEMENTATION

## WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

A technology stack is a set of frameworks and tools used to develop a software product. This set of frameworks and tools are very specifically chosen to work together in creating a well-functioning software.

Firstly, I created an EC2 in Asia Pacific region Tokyo.

Let me list certain parameters when choosing an AWS region which factors should you consider:

* Latency and proximity

* Security and regulatory compliance

* Service Level Agreements (SLA)

And finally, the most important is the **cost**

<img width="404" alt="Asia pacific" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/f6d6d45a-049e-4ff9-b637-fc9cf3fa2079">


### Click on "Services" at the upper left corner and you will see the all the Services available on AWS. Click on "EC2"

<img width="542" alt="ec2" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/4a8ed69a-6dd6-4d08-b235-77250c69477b">

## select ec2 stroll down, and Click on "Launch Instance."

<img width="890" alt="launch ins" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/6c617226-062e-403b-a83e-ca6cf1feb007">



## Click on Next: to choose an instance type

<img width="605" alt="instance type" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/d2c113e3-4639-4273-b0a3-886cb5fbfd3d">

## Next: Select a keypair

<img width="625" alt="keypair " src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/3e4a7d1f-74b9-40ff-bbdb-2450b309f6c0">

## Next: Configure Instance Details by creating or adding an existing security group

<img width="590" alt="Screenshot 2023-06-05 075828" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/e00e00ed-92fb-4852-b47f-89961cd2388d">

**Next:**  Add Storage; to add or configure the Storage size and type. Every time you launch an instance from an AMI, a root storage device is created for that instance. The root storage device contains all the information necessary to boot the instance. You can specify storage volumes in addition to the root device volume when you create an AMI or launch an instance using block device.

<img width="602" alt="Screenshot 2023-06-05 080038" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/871f336d-8b1f-4966-aa4b-d5769f70a36c">

The next phase is to view your instance state, click on your instance to view it. At this stage, you will see if your instance is running or still pending. mine is running, now i can view my instance details

<img width="1262" alt="Screenshot 2023-06-05 080702" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/51c16be6-8ba1-482e-a09b-cdd71a33ca30">

**Next** I opened my MOBAXTERM, choose Ubuntu-22.04. 

<img width="1277" alt="Screenshot 2023-06-05 081921" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/28751386-b9bb-4f25-a4e4-f5cb10f2cea2">

**Next**: Although, I have my keypair stored in a folder named **soso** I cd into the folder **soso** then connect to the instance using the link

<img width="699" alt="Screenshot 2023-06-05 082703" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/9e9e4ce2-bbc2-4ffc-ab6d-51140cdd88be">


<img width="1262" alt="Screenshot 2023-06-05 082844" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/20e597b6-335f-4794-81ca-1f0f03c826fc">


For a web application to work smoothly, it has to include an operating system, a web server, a database, and a programming language. The name LAMP is an acronym of the following programs:



```
* Linux Operating System
* Apache HTTP Server
* MySQL database management System
* PHP programming language
```

### In this project, I will implement a web solution based on LAMP stack on a Linux server by implementing the steps below:



# Step 1 — Installing Apache and Updating the Firewall
* We need to Install Apache using Ubuntu’s package manager, apt:


```
$ sudo apt update

$ sudo apt install apache2
```


**To verify that apache2 is running as a Service in our OS, use following command**

```
 sudo systemctl status apache2
 
 ```
 
 
 <img width="1267" alt="Screenshot 2023-06-05 084231" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/e141fc4c-d2bf-445d-880d-e6bcc1082166">

 
Before we can receive any traffic by our Web Server, we need to open TCP port 80 which is the default port that web browsers use to access web pages on the Internet
 
To open our port 80, i went back to the instance, clicked on security, clicked on edit inbound rules and i add rules. i added port 80 for http and port 443 https and i cliked on save rules


<img width="1100" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/ff91b863-98c5-43bc-a514-96cab2167722">


## The server is running and we can access it locally and from the Internet (Source 0.0.0.0/0 means ‘from any IP address’).
 
* To verify and check that I can access it locally in our ubuntu shell and from the internet, run:

```
$ curl http://localhost:80
or
$ curl http://127.0.0.1:80
```

**As an output you can see some strangely formatted test, do not worry, we just made sure that our Apache web service responds to ‘curl’ command with some payload.**


Open a web browser of your choice and try to access following url


```
http://<Public-ip-address>:80
```


* If you see the following page, then your web server is now correctly installed and accessible through your firewall. 


**see my output:**

<img width="938" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/0a5d434e-d6f2-4831-95ae-ca6ae5f5bed8">

# STEP 2 - Installing MySQL

### We need to install the database system to be able to store and manage data for our website. MySQL is a popular database management system used within PHP environments.

* To install mysql-server, run:

```
sudo apt -y install mysql-server
```

* After the installation it is recommended that we run a security script that comes pre-installed with MySQL. This script will remove some insecure default settings and lockdown access to our database system.
* Start the interactive Script by running:


```
sudo mysql_secure_installation
```


* This will ask if you want to configure the VALIDATE PASSWORD PLUGIN.


## Note: Enabling this feature is something of a judgment call. If enabled, passwords which don’t match the specified criteria will be rejected by MySQL with an error. It is safe to leave validation disabled, but you should always use strong, unique passwords for database credentials.




Answer Y for yes, or anything else to continue without enabling.


```
VALIDATE PASSWORD PLUGIN can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD plugin?

Press y|Y for Yes, any other key for No:
```

* If you answer “yes”, you’ll be asked to select a level of password validation. Keep in mind that if you enter 2 for the strongest level, you will receive errors when attempting to set any password which does not contain numbers, upper and lowercase letters, and special characters, or which is based on common dictionary words.



### <p> If we enabled password validation, we’ll be shown the password strength for the root password we just entered and our server will ask if we want to continue with that password. If we are happy with our current password, enter Y for “yes” at the prompt:</p>



### For the rest of the questions, We press Y and hit the ENTER key at each prompt. This will remove some anonymous users and the test database, disable remote root logins, and load these new rules so that MySQL immediately respects the changes we have made.



when you are done, you will get this **output:** 

<img width="378" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/218b96fc-2d3c-4dfa-a72c-c4740e83d8d2">


* When you're finished, test if you're able to login to the MySQL Console by typing:

```
sudo mysql
```

<img width="371" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/df1c9cee-b6e4-4a74-a88a-a7a2fc852621">




* To exit the MySQL Console, type: exit

```
mysql> exit
```

### Setting a password for the root MySQL account works as a safeguard, in case the default authentication method is changed from unix_socket to password. For increased security, it’s best to have dedicated user accounts with less expansive privileges set up for every database, especially if we plan on having multiple databases hosted on our server.


### *Note*: At the time of this writing, the native MySQL PHP library mysqlnd doesn’t support caching_sha2_authentication, the default authentication method for MySQL 8. For that reason, when creating database users for PHP applications on MySQL 8, we’ll need to make sure they’re configured to use mysql_native_password instead. We’ll demonstrate how to do that later.


### Our MySQL server is now installed and secured.


* Next, we will install PHP, the final component in the LAMP Stack.



## Step 3 — Installing PHP


### We have Apache installed to serve our content and MySQL installed to store and manage our data. PHP is the component of our setup that will process code to display dynamic content to the final user. In addition to the php package, we’ll need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. We’ll also need libapache2-mod-php to enable Apache to handle PHP files. Core PHP packages will automatically be installed as dependencies.


* To install these 3 packages at once, run:


```
$ sudo apt -y install php libapache2-mod-php php-mysql
```

* Once the installation is finished, you can run the following command to confirm your PHP version:

```
php -v
```

<img width="500" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/259a4dce-5164-45ad-8a57-8e326bc719b3">


* At this point, your LAMP stack is completely installed and fully operational.
* To test our setup with a PHP Script, it's best to setup a proper Apache Virtual Host to host our website's file and folders.
Virtual Host allows you to have multiple websites located on a single machine and users of the websites will not even notice it.


<img width="744" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/95ec81cb-1aa2-4f59-908c-dd9a88bfc127">



* We will configure our first Virtual Host in the next step.



## Step 4 — Creating a Virtual Host for your Website using Apache

In this project, you will set up a domain called projectlamp, but you can replace this with any domain of your choice.


Apache on Ubuntu 20.04 has one server block enabled by default that is configured to serve documents from the /var/www/html directory. We will leave this configuration as is and will add our own directory next next to the default one.


Create the directory for projectlamp using ‘mkdir’ command as follows:

```
sudo mkdir /var/www/projectlamp
```

Next, assign ownership of the directory with the $USER environment variable, which will reference your current user.

```
$ sudo chown -R $USER:$USER /var/www/projectlamp
```

* We can now open a new configuration file in Apache’s sites-available directory using our preferred command-line editor. Here, we’ll be using vi

```
$ sudo vi /etc/apache2/sites-available/projectlamp.conf
```

This will create a new blank file. Paste in the following bare-bones configuration by hitting on i on the keyboard to enter the insert mode, and paste the text:



<img width="532" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/0d86e395-49a3-4c2a-b209-ab92100c4b33">



To save and close the file, simply follow the steps below:

* Hit the esc button on the keyboard
* Type :
* Type wq. w for write and q for quit
* Hit ENTER to save the file


#### You can use the *ls* command to show the new file in the sites-available directory

```
$ sudo ls /etc/apache2/sites-available
```


* see my output


<img width="475" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/6513837a-cfd4-4b14-9b75-7edcf3e42a12">



### With this VirtualHost configuration, we’re telling Apache to serve propitixhomes.local using */var/www/projectlamp* as the web root directory. If we like to test Apache without a domain name, we can remove or comment out the options ServerName and ServerAlias by adding a # character in the beginning of each option’s lines. Adding the # character there will tell the program to skip processing the instructions on those lines.



You can now use a2ensite command to enable the new virtual host:

```
$ sudo a2ensite projectlamp
```


<img width="404" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/6553bc8a-186d-451c-8f5e-127386a38a4c">


* We might want to disable the default website that comes installed with Apache. This is required if we are not using a custom domain name, because in this case Apache’s default configuration would overwrite our virtual host. To disable Apache’sdefault website use a2dissite command, type:


```
$ sudo a2dissite 000-default
```

<img width="352" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/032cb8e8-6668-4b9b-8873-193193cf38e7">



* To make sure your configuration file doesn't contain syntax errors, run :

```
$ sudo apache2ctl configtest
```

<img width="482" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/04609b1b-02e6-4231-8bdd-51cd223e28f5">


* Finally, reload Apache so these changes take effect:

```
$ sudo systemctl reload apache2
```


Your new website is now active, but the web root /var/www/projectlamp is still empty. Create an index.html file in that location so that we can test that the virtual host works as expected:


* Type and run :

```
$ sudo vi /var/www/projectlamp/index.html
```

see my input :

<img width="557" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/1d92cf6d-3954-4f6c-aecb-c9c41dbec564">


Now go to your browser and try to open your website URL using IP address:

```
http://<public-ip-address>:80
```
or you can also browse using your public dns. the result is the same

```
http://<Public-DNS-Name>:80
```

see my output :

<img width="562" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/03fa23fe-608c-4d4d-9836-bd8d97b405b0">


You can leave this file in place as a temporary landing page for your application until you set up an index.php file to replace it. Once you do that, remember to remove or rename the index.html file from your document root, as it would take precedence over an index.php file by default.


* To check your Public IP from the Ubuntu shell, run :

```
$(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 
$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4)
```


## Step 5 — Enable PHP on the website


With the default DirectoryIndex settings on Apache, a file named index.html will always take precedence over an index.php file. This is useful for setting up maintenance pages in PHP applications, by creating a temporary index.html file containing an informative message to visitors. Because this page will take precedence over the index.php page, it will then become the landing page for the application. Once maintenance is over, the index.html is renamed or removed from the document root, bringing back the regular application page.

In case you want to change this behavior, you’ll need to edit the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive:

```
sudo vim /etc/apache2/mods-enabled/dir.conf
```

<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>


After saving and closing the file, you will need to reload Apache so the changes take effect:

```
$ sudo systemctl reload apache2
```


* Finally, we will create a PHP Script to test the PHP is correctly installed and configured on our Server.
* Now that we have a custom location to host our website's files and folders, we'll create a PHP test script to confirm that Apache is able to handle and process requests for PHP files.
* Create a new file named index.php inside our custom web root folder:

```
$ vim /var/www/projectlamp/index.php
```

This will open a blank file. Add the following text, which is valid PHP code, inside the file:

```
<?php
phpinfo();
```

<img width="1095" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/53899d91-5ae1-4b65-9c38-03a2e91d04fe">


## When you are finished, save and close the file, refresh the page and you will see a page similar to this :


<img width="1091" alt="image" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/f11222c6-0181-4fe7-accf-1cc4cd9f63a8">


**This page provides information about your server from the perspective of PHP. It is useful for debugging and to ensure that your settings are being applied correctly**.

**If you can see this page in your browser, then your PHP installation is working as expected**.

**After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment -and your Ubuntu server. You can use rm to do so:**


```
$ sudo rm /var/www/projectlamp/index.php
```







































