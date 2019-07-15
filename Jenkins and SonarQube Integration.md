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
 - Then, Go to Configure Global Tools and Search for SonarQube Scanner and click on  add a sonarqube scanner installation give name and uncheck install automatically and input the path of the installed sonarqube scanner path **ex:/opt/sonarscanner/sonar-scanner-4.0.0.1744-linux/**
 - and save the settings
 
## Step 4: Configuring SonarScanner MSBuild Installation
 - Before Configuring SonarScannerMSBuild Installation in Jenkins you need to install and configure on your machine
   Download Sonar Scanner for MSBuild from the [link](https://github-production-release-asset-2e65be.s3.amazonaws.com/34444711/86426b00-8213-11e9-8f88-703c2f5a2213?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20190715%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20190715T093458Z&X-Amz-Expires=300&X-Amz-Signature=c03a4bf86f05e624601322bcbf77e367303a89fc222d43ec23afca024ed5a6dc&X-Amz-SignedHeaders=host&actor_id=18532675&response-content-disposition=attachment%3B%20filename%3Dsonar-scanner-msbuild-4.6.2.2108-net46.zip&response-content-type=application%2Foctet-stream) and copy it to /opt/ folder
 - Then, Go to Configure Global Tools and Search for SonarQube Scanner for MSBuild and Click on add installation give a Name to it and add path to your SonarScanner MSBuild Folder **ex:** /opt/SonarScanner.MSBuild/ make sure you give executable permission to SonarScanner.MSBuild.exe in SonarScanner.MSBuild folder 
   ```bash
   chmod +x /opt/SonarScanner.MSBuild/SonarScanner.MSBuild.exe
   ```
 - and save the settings<br/>
## NOTE:
 - For SonarScanner for MSBuild make sure you have installed latest mono-devel and nuget, For mono installation go through this [doc](https://github.com/adityayavagal/CI-CD-Server-Setup/blob/master/MSBuild%20Linux%20Installation.md)
 - Also make sure for all these folders sonarqube user is owner
 - For more information read [SonarQube Doc](https://docs.sonarqube.org/latest/) and for video tutorial try [youtube](https://youtu.be/jh7utASgKj4)
