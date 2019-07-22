# Upload artifact to nexus using Jenkins

## For Maven Projects 
  - Before uploading the artifact make sure it is built and there in workspace
  - In build section in build step click on Nexus artifact uploader
  - Then in the form select the version of the repository that you want to upload to
  - Select protocol
  - Enter URL of the repository
  - Give the Credentials
  - Enter the Group Id as you want to store
  - Enter Version
  - Enter the repository name
  - In artifact section click on add
  - Enter artifact Id as you want to save
  - In type enter the artifact extension **ex:** jar, war, zip
  - In file section Enter the path to where artifact is stored

## For .NET Projects
  - The procedure for .Net Projects is same but zip the folder you want to upload and pass it to nexus artifact uploader
  - **Ex:** ```cd Projectfolder/bin/Release && zip -r my.zip *``` and pass the zip files path to artifact uploader
