# Execute SonarQube Scan

## For Maven Projects
  - In build section click on build step and add **Execute SonarQube Scanner**
  - Select SonarQube Scanner Installation in the drop down and supply arguments if any else make sure you setup **sonar-project.properties** file in root of your project
 
## For MSBuild Projects
  - In build section click on build step and add **SonarScanner for MSBuild - Begin Analysis**
  - Enter the project key and name you created in SonarQube and enter the project version
  - Next, click build step and add execute shell and enter ```msbuild /t:rebuild```
  - Next, click build step and add **SonarScanner for MSBuild - End Analysis**
