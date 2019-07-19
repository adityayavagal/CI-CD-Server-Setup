# Integration Jenkins with Nexus Repository Manager
  - Go to Jenkins plugin manager and install Nexus artifact Uploader Plugin.
  - For safety create a Jenkins user in Nexus only with required permissions
  - Add those credentials in Jenkins credentials
  
# Creating a Build Job to upload artifact to Nexus
  - In Build Section of the Free style Project after your all build step add Nexus artifact uploader step
  - Select Nexus version 3
  - Protocol HTTP
  - Enter URL of the Nexus Repository without http as prefix **Ex:** 192.168.0.254:8081 or nexusrepo.com
  - In Credentials section select the credentials you add previously for Nexus Server
  - Enter the Group Id **ex:** Aequs
  - Enter Version
  - In repository section Enter the repository you want to upload the artifact to
  - Click on add artifact
  - In artifact section add the artifact name **ex** Dashboard/ Server
  - In type Enter the file type you want to upload
  - In File Enter the path to your Artifact
  - Save the changes to job

**Plugin**[Nexus Artifact uploader](https://wiki.jenkins.io/display/JENKINS/Nexus+Artifact+Uploader)
