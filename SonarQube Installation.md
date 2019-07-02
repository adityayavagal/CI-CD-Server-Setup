# Setting up SonarQube for continuous inspection of code quality

## PostgreSQL Setup on Ubuntu 18.04

Postgres, is a relational database management system that provides an implementation of the SQL querying language. It is a popular choice for many small and large projects and has the advantage of being standards-compliant and having many advanced features like reliable transactions and concurrency without read locks.

### Step 1 - Installation

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
```

### Step 2 - Using PostgreSQL  Roles and Databases

Switch to Over to PostgreSQL account using
```bash
sudo -i -u postgres
```
To Enter the shell type
```bash
psql
```

Alternatively, to enter psql Shell directly
```bash
sudo -u postgres psql
```
#### Note: 
1. For Postgres Tutorials Follow This [Link](https://www.tutorialspoint.com/postgresql)
2. For Accessing Postgres remotely Follow This [Link](https://blog.bigbinary.com/2016/01/23/configure-postgresql-to-allow-remote-connection.html)

### Step 3 - Creating our Sonarqube db user

First Enter postgres user, Create user using following command
```bash
create user sonarqube
```
Next, Enter psql Shell with psql command and Create password and database for the user
```bash
ALTER USER sonarqube WITH ENCRYPTED password 'password';
CREATE DATABASE sonar OWNER sonarqube;
```
and quit shell by typing
```bash
\q
```

## Installing and Configuring SonarQube


### Step 1 - Create a ubuntu user with name sonar
```bash
sudo adduser sonar
```
### Step 2 - Download the Latest SonarQube(LTS versions are recommended)
#### Note:
While installing this software current LTS version v6.7 was going obsolete and was going to be replaced by v7.9 so we are going installed v7.7 (please check the latest LTS version and release notes before installation)
```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-7.7.zip
```
### Step 3 - Unzip file
```bash
unzip sonarqube-7.7.zip
```
### Step 4 - Copy extracted folder to /opt Folder
```bash
sudo cp -r sonarqube-7.7 /opt/sonarqube
```
### Step 5 - Change ownership of the folder
```bash
sudo chown -R sonar:sonar /opt/sonarqube
```
### Step 6 - To run SonarQube you need configure this file
```bash
sudo nano /opt/sonarqube/bin/linux-x86-64/sonar.sh
```
and find ```bash RUN_AS_USER=sonar``` and make sure it's not commented and the username you created before if not enter the user you create

### Step 7 - Configuring SonarQube Database configurations
```bash
sudo nano /opt/sonarqube/conf/sonar.properties
```
and make following changes
```bash
sonar.jdbc.username={sonarqubeDBUser}
sonar.jdbc.password={SonarqubeDBUserPassword}
sonar.jdbc.url=jdbc:postgresql://localhost/{DBforSonarQube}
sonar.web.host=127.0.0.1
sonar.search.javaOpts=-Xms512m  -Xmx512m
```
### Step 8 - Create a Service file for SonarQube
Create Service file to manage SonarQube service
```bash
sudo nano /etc/systemd/system/sonar.service
```
Enter the following lines:
```bash
[Unit]
Description=SonarQube service
After=syslog.target network.target

[Service]
Type=forking

ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start
ExecStop=/opt/sonarqube/bin/linux-x86-64/sonar.sh stop

User=sonar
Group=sonar
Restart=always

[Install]
WantedBy=multi-user.target
```
save and close, start and enable the service with following command
```bash
sudo systemctl start sonar
sudo systemctl enable sonar
```
You can check the status by following command
```bash
sudo systemctl status sonar
```
now, you can access sonaqube from 127.0.0.1:9000 or youripaddress:9000
#### Note: If you can't access the SonarQube please check for log files in /opt/sonarqube/logs folder has logs of everything

#### References:
\[1\] [https://www.howtoforge.com/how-to-install-sonarqube-on-ubuntu-1804/](https://www.howtoforge.com/how-to-install-sonarqube-on-ubuntu-1804/)  
\[2\] [https://docs.sonarqube.org/latest/setup/install-server/](https://docs.sonarqube.org/latest/setup/install-server/)
