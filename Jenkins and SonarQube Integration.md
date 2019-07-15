# Integration SonarQube with Jenkins

## Step 1:  Install SonarQube Plugin for Jenkins
**Plugin:**```SonarQube Scanner for Jenkins```

## Step 2: Configure SonarQube Server Installation
 - Go to Manage Jenkins
 - Then, Configure System
 - Search for SonarQube Server and Click on Add SonarQube
 - Enter the required Information such as Name, URL and provide the Authentication token of sonarqube User

## Step 3: Configuring SonarScanner Installaion
 - Before Configuring Sonar Scanner in Jenkins you need to install and configure on your machine 
   ```bash
   wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.0.0.1744-linux.zip
   mkdir /opt/sonarscanner
   unzip sonar-scanner-cli-4.0.0.1744-linux.zip
   mv sonar-scanner-cli-4.0.0.1744-linux /opt/sonarscanner
   sudo ln -s /opt/sonarscanner/sonar-scanner-3.2.0.1227-linux/bin/sonar-scanner /usr/local/bin/sonar-scanner
   ```
 - Then, Go to Configure Global Tools and Search for SonarQube Scanner and click on  add a sonarqube scanner installation give name and uncheck install automatically and input the path of the installed sonarqube scanner path **ie:/opt/sonarscanner/sonar-scanner-4.0.0.1744-linux/**
 - and save the settings
 
 
