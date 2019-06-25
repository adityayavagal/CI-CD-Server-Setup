# Installing Nexus Repository Manager

## Nexus Repository Manager
Nexus is a repository manager. It allows you to proxy, collect, and manage your dependencies so that you are not constantly juggling a collection of JARs. It makes it easy to distribute your software. Internally, you configure your build to publish artifacts to Nexus and they then become available to other developers. You get the benefits of having your own 'central', and there is no easier way to collaborate.

### Step 1 - Download Latest nexus repository tar.gz file
```bash 
wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
```
### Step 2 - Add user nexus
```bash
sudo adduser nexus
```
### Step 3 - Create Installation directory for Nexus
```bash
sudo mkdir /opt/nexus
```

### Step 4 - Move Downloaded file to installation folder and extract the contents
```bash
sudo mv latest-unix.tar.gz /opt/nexus/
sudo tar xvzf latest-unix.tar.gz
sudo rm latest-unix.tar.gz
```
### step 5 - Change the owner of nexus installation directory
```bash
sudo chown -R nexus:nexus /opt/nexus/
```

### step 6 - Edit nexus.rc file and update the file like given below
```bash
run_as_user="nexus"
```

### step 7 - Create a Service to run nexus as service
```bash
sudo nano /etc/systemd/system/nexus.service
```
Enter the following code and save the file
```bash
[Unit]
Description=Nexus service
After=syslog.target network.target

[Service]
Type=forking
LimitNOFILE=65536
ExecStart=/opt/nexus/nexus-3.17.0-01/bin/nexus start
ExecStop=/opt/nexus/nexus-3.17.0-01/bin/nexus stop

User=nexus
Group=nexus
Restart=always

[Install]
WantedBy=multi-user.target
```
### Step 8 - Enable and start the service
```bash
systemctl start nexus.service
systemctl enable nexus.service
```

### Step 9 - Login for the first time
By default the nexus server runs on 8081 port you can go to browser and access by typing <NexusServerIP>:8081

#### Note: When you access the server for the first time you should login using default username and password 
```bash
Username: admin
Password: Stored in <yourInstallationDir>/sonatype-work/nexus3/admin.password
```
#### Password will be stored in \<nexusDir>/sonatype-work/nexus3/admin.password copy its contents in passowrd file and you will be logged in
