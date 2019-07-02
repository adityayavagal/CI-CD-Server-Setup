# Installing gitea Version Control

## What is Gitea ?
Gitea is a painless self-hosted Git service. It is similar to GitHub, Bitbucket, and GitLab. Gitea is a fork of Gogs. 

## prerequisites
**SQL:** MySQL, SQLite, PostgreSQL(Recommended) 
**VCS:** git(required)

### Step 1: Download gitea binary
```bash
wget -O gitea https://dl.gitea.io/gitea/1.8.3/gitea-1.8.3-linux-amd64
chmod +x gitea
```

### Step 2: Create user to run gitea
```bash
adduser \
   --system \
   --shell /bin/bash \
   --gecos 'Git Version Control' \
   --group \
   --disabled-password \
   --home /home/gitea \
   gitea
```

### Step 3: Create Required File Structure
```bash
mkdir -p /var/lib/gitea/{custom,data,log}
chown -R gitea:gitea /var/lib/gitea/
chmod -R 750 /var/lib/gitea/
mkdir /etc/gitea
chown root:git /etc/gitea
chmod 770 /etc/gitea
```
### Step 4: Copy gitea binary to Global Location
```bash
cp gitea /usr/local/bin/gitea
```
### Step 5: Running gitea as Service
```bash
sudo vim /etc/systemd/system/gitea.service
```
copy sample [gitea.service]()

### Step 6: Enable and start gitea service
```bash
sudo systemctl enable gitea
sudo systemctl start gitea
```
### Step 7: Initial Setup
Initially gitea will be running on PORT 3000 you can visit it by http://<ip_address>:3000/install and do the required configurations and submit

### Step 8: Admin Login
First User to register to gitea will be admin 

**Note:** This document follows the steps given in gitea [website](https://docs.gitea.io/en-us/install-from-binary/)
