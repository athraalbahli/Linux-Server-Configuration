# Linux-Server-Configuration
Fifth Project on Udacity full stack developer nanodegree


* IP Address: 167.99.195.132
* URL: http://iathra.com/

## Steps
- Create a new ubuntu server using digiatlocean (Ubuntu 16.04 LTS.)
- Login as root using an inital password provided by email
- Change the password
- Create a non-root user with sudo privilege and Configure key-based authentication
 ```
 adduser grader
 usermod -aG sudo grader
 nano /etc/sudoers.d/grader
 ```
 add this line 
  ```
  grader ALL=(ALL) NOPASSWD:ALL
  ```
- Prevent root user form login and prevent login using password
 ```
  /etc/ssh/sshd_config
 ```
- Update the server packeges
```
  sudo apt-get update
  sudo apt-get upgrade
```
- login as non-root user
- Install apache
```
  sudo apt-get install apache2
```
- Install and configure PostgreSQL
```
  sudo apt-get install libpq-dev python-dev
  sudo apt-get install postgresql postgresql-contrib
```
- Insatll and enable mod_wsgi
```
  sudo apt-get install libapache2-mod-wsgi python-dev
  sudo a2enmod wsgi
```
- Clone the catalog application from github
- Create a wsig file for the flask application
- Setting up a virtual environment to install the application package inside it
```
 sudo pip install virtualenv 
 sudo virtualenv venv
```
- Install flask and its dependencies inside the virtual environment
- Configure and enable new virtual host on apache to serve the flask application
```
  sudo nano /etc/apache2/sites-available/catalogApp.conf
```
- Update path of client_secrets.json file
- Update the db engine to postgresql
- Configure firewall rules
```
  sudo apt-get install ufw
  sudo ufw allow 80/tcp
  sudo ufw default deny incoming
  sudo ufw default allow outgoing
  sudo ufw allow 2200/tcp
  sudo ufw allow ntp
  sudo ufw enable
 ```

## grader user
- location of ssh key is: /home/grader/.ssh/authorized_key
- the sudo password is provided in the student note tab

## Resources
- [How To Deploy a Flask Application on an Ubuntu VPS](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
- [How To Create a Sudo User on Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart)
