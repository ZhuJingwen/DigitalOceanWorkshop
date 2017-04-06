# DigitalOcean Workshop
This is a collection of code examples and step-by-step instructions on setting up a DigitalOcean droplet for node.js projects.

# DigitalOcean Set up

## Part I: Set up accounts
1. Get the [GitHub Student Developer Pack](https://education.github.com/pack)
2. Register a [DigitalOcean](https://www.digitalocean.com/) account
3. Use the code from Github Student Developer Pack in DigitalOCean [Billing](https://cloud.digitalocean.com/settings/billing) Settings Promo Code section to get $50 credits

## Part II: Create a droplet
1. Click Create Droplet
2. Choose an image: select NodeJS 6.9.5 on 16.04
![select NodeJS 6.9.5 on 16.04]
(https://cloud.githubusercontent.com/assets/5662216/24776782/4fe6b106-1af0-11e7-9729-ee50fbef6936.png)
3. Choose the smallest size $5/mo
![select $5/mo](https://cloud.githubusercontent.com/assets/5662216/24776874/c866d7e6-1af0-11e7-8691-3489cd27af76.png)
4. Choose a datacenter region 
![Choose a datacenter region](https://cloud.githubusercontent.com/assets/5662216/24776899/e6464a58-1af0-11e7-8e42-3a16e65e7ff5.png)
5. Choose a hostage name: give it any name you want
6. Click Create
7. After a while, you should have received an email of your first time log in info.

## Part III: Set up users
1. In the email from DigitalOcean, you should have your credentials for the new droplet, including IP address, username "root" and password.
2. Using Terminal on Mac to connect to your droplet. You need to use the password in the email for the first time login, and then you can set up your own password.
3. In Terminal, type:
```
ssh root@YOUR_IP_ADDRESS
```
4. Copy and paste the password from the email, and then set your own password for user "root" as it prompts.
5. For security, it's better to create a user separate from root. Give your self an username, then in Terminal, type:
```
adduser YOUR_USERNAME
```
6. To give the user administrator privileges, you need to set the user as a sudo user:
```
usermod -aG sudo YOUR_USERNAME
```
7. Then you are all set. Switch to the user you just set up, then you could run projects on it:
```
su - YOUR_USERNAME
```

## Part IV: Transfer Files
1. Download [Cyberduck](https://cyberduck.io/?l=en)
2. In Cyberduck, click open connection
3. Select SFTP(SSH File Transfer Protocol)
4. Type your IP address in Sever box, your username in Username box, and password:
![Type your IP address in Sever box, your username in Username box, and password](https://cloud.githubusercontent.com/assets/5662216/24777567/f028f5ea-1af3-11e7-87f7-b4e6c62e6ee8.png)
5. Click connect
6. Drag your project into Cyberduck

## Part V: Run your project
1. In Terminal, make sure that you are logged in as the user you created, then typ:
```
USERNAME@DROPLET_NAME:~$ ls
```
You should see the project you just dragged into Cyberduck
2. Change directory to the project:
```
USERNAME@DROPLET_NAME:~$ cd YOUR_PROJECT_FOLDER_NAME
```
In this case: 
```
USERNAME@DROPLET_NAME:~$ cd socket-example
```
3. Install node modules:
```
USERNAME@DROPLET_NAME/socket-example:~$ npm install
```
4. Run the project:
```
USERNAME@DROPLET_NAME/socket-example:~$ node server.js
```
5. In browser, go to [YOUR_IP_ADDRESS: YOUR_PORT_NUMBER](YOUR_IP_ADDRESS: YOUR_PORT_NUMBER)
In this case: [YOUR_IP_ADDRESS: 8080](YOUR_IP_ADDRESS: 8080)

### Run your project on default HTTP port
1. In Cyberduck, open server.js file with a text editor, change port 8080 to 80(default Hypertext Transfer Protocol(HTTP))
2. In Terminal, Type:
```
USERNAME@DROPLET_NAME/socket-example:~$ sudo node server.js
```
3. In browser, go to [YOUR_IP_ADDRESS](YOUR_IP_ADDRESS)

## Part VI: Run the project forever
1. You might notice that now if you quit Terminal, the project would stop running. So we need to set it to run foever.
2. Ctrl + C to stop the server
3. Installing forever module:
```
USERNAME@DROPLET_NAME/socket-example:~$ sudo npm install -g forever 
```
4. Run the server forever:
```
USERNAME@DROPLET_NAME/socket-example:~$ sudo forever start server.js
```
5. All set! Now if you quit Terminal, the project would continue running. For more details about forever.js, please check [here](https://github.com/foreverjs/forever)

### Advanced
- [Use SSH keys](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)
- [Set up a host name](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-host-name-with-digitalocean)
