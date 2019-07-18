# Integrating Jenkins with Github(Building Project after each commit)

## Installing Plugin
  - Go to Jenkins and search for **Github Integration Plugin** Install it.
  
## Generate ssh key 
  - Go to Terminal and switch to jenkins user and generate a ssh, leave everything default and don't enter passphrase
    ```bash
    sudo su jenkins
    ssh-keygen
    ```
  - Display the public key of your ssh key
    ```bash
    cat ~/.ssh/id_rsa.pub
    ```
  - Copy the public you just displayed and go to your github account and add access key to your account
    - settings -> SSH and GPG keys -> New SSH key
    
  - Display your secret key and add in jenkins
    - ```bash cat ~/.ssh/id_rsa```
    - Open jenkins and Go to Credentials and credentials
    - Change the kind to **SSH Username with private key**
    - Give  ID and name and in private key option select Enter directly and paste the private key you just displayed
    
## Building the Job whenever Code is pushed to Github
  - Go settings of your project and select webhooks
  - Click on Add webhook
  - In URL field Enter: **http://\<your-public-ip-or-domain-name-where-jenkins-is-running>/github-webhook/**
  - Select Content Type as **application/json**
  - Make sure **Just the push event** is selected
  - Click on save webhook
  
## Creating the Jenkins Job
  - Create a free style job and in project Configuration
  - In general section add your github project URL
  - In Source code management section select and Enter your git repo url **i.e:https://github.com/username/project.git** or **git@github.com:username/repo.git**(When your using private repo use second example as first example works only with public repo, select ssh key credential if you're using private repository and select the branch you want to monitor pushes
  - In Build Triggers section select **Github hook trigger for GITScm polling**
  - Next, In build section you can add your build steps and save.
  
**NOTE:**
  - Make sure your jenkins instance has public ip or is exposed to a domain name in order to integrate with github
  - Adding SSH key section is only mandatory when you are working with private repositories
  - Make sure all the above github procedures are done by the project owner or admin of the project in github
  - References [link1](https://youtu.be/Z3S2gMBUkBo) [link2](https://youtu.be/HTlAssPBKBs)
