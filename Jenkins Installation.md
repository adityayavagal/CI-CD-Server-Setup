# Installing Jenkins CI 

## Jenkins
Jenkins is an open source automation server that offers an easy way to set up a continuous integration and continuous delivery (CI/CD) pipeline.

## Prerequisites
Before continuing with this tutorial, make sure you are logged in as a user with sudo privileges.

## Installing Jenkins

### Step 1: Install Java
```bash
sudo apt update
sudo apt install openjdk-8-jdk
```

### Step 2: Add Jenkins Debian Repository
```bash
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```
**Next**, add Jenkins repository to system with
```bash
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

### Step 3: Installing Jenkins
```bash
sudo apt update
sudo apt install jenkins
```
Jenkins service will automatically start after installation you can verify by  printing service status
```bash
systemctl status jenkins
```
You should see something like this
```bash
● jenkins.service - LSB: Start Jenkins at boot time
Loaded: loaded (/etc/init.d/jenkins; generated)
Active: active (exited) since Wed 2018-08-22 1308 PDT; 2min 16s ago
    Docs: man:systemd-sysv-generator(8)
    Tasks: 0 (limit: 2319)
CGroup: /system.slice/jenkins.service
```
### Step 4: Adjust Firewall (Optional if firewall is inactive)
Assuming your using ufw you can enable remote access by
```bash
sudo ufw allow 8080
```
**Next**, verify change with:
```bash
sudo ufw status
```
```bash
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
8080                       ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
8080 (v6)                  ALLOW       Anywhere (v6)
```
### Step 5: Setting up Jenkins
To setup your Jenkins installation, open your browser, type your domain or IP and followed by port 8080, http://your_ip_or_domain:8080 and youll be asked to enter initial admin password to which path will given there itself (eg:/var/lib/jenkins/secrets/initialAdminPassword)<br/>
**Next**, Display the file contents
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
```bash
2115173b548f4e99a203ee99a8732a32
```
Copy the password from terminal and paste into administrator password field and click continue and choose the suitable settings for you and follow the steps

**Note:** This installation follows the steps given in this [link](https://linuxize.com/post/how-to-install-jenkins-on-ubuntu-18-04/#installing-jenkins)
