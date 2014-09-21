##  magento on the go
==============

Magento with db manager running easily in just one build / run.

### What's bundled :
- Magento 1.9.0.1
- Adminer (Db Manager)
- Ubuntu 14.04 with shell access
- AMP (Apache (2.0) / Php (5.5.9) / Mysql)
- Supervisor [to keep them up and running all time]

### How to build :
Get into your server with SHELL access. And run a git pull which follows
> git clone https://github.com/ilampirai/magentoonthego.git .

This will get basic files for building our git image. Then start the build using
> docker build -t {sitename}/magento .
NOTE: There is a tiny little dot in the end

This will take some time wait till the docker finish building. Once done Docker will bring a success message. (50% of work done :) )

### How to run :
Using the docker image we build we can bring the server up in seconds. 

Just execute the final shell command  
> docker run -d -p 80:80 -p 2222:22 {sitename}/magento

This gives a container ID and your new magento is ready to be installed.

### Installing Magento :
Haha Not going to tell you the whole process just the starting point, Hoping you know the rest.

Open a browser and type 
> http://your.ip.address-or-sitename.com/

You can see a brand new magneto waiting to be installed.

Proceed the magento setup and when you are in need of Database details,
There are two users for us to choose.
First is our default root user with only the localhost connection, the logins are 
> root / unknown

Second is the user with normal access from other servers to external user admin
to find your password for admin you must type 
> docker ps
which shows the running containers note down the id
Then run
docker logs {container id}

That will print down the password like 

mysql -uadmin -pXXXXXXXXXXX -h<host> -P<port>

you can use any account since we are running magento only from localhost.

After finding out the password or using root account goto 
> http://your.ip.address-or-sitename.com/adminer.php
NOTE : In a separate tab

Enter the login info and you will get your Database Manager. 
Create a new database for Magento and use this info in Magento installation process and proceed. 

Thats it your site now running!!!!

### Shell Access to your Magento :
To access files you can use the shell access with 
- Host : your site ip or domain
- Port : 2222
- User : root
- Pass : admin123

Make sure you change the password on first login this is just a easy password that anyone can hack.
> passwd
this will help you set new password.

That's the full story for now and this is not the end some updates like 
- File Editor
- Selected version of magento
- Browser Terminal
are in development phase and will be added soon.

Thanks to tutum-docker for LAMP, That gave me a good start.












