# Setup a Project for CICD

**Tools used:** Github, SonarQube, Nexus Repository, Jenkins

## 1. Create a Project in SonarQube and note the Project name 
## 2. Create a Repository in Nexus if you don't have a repository where it can be published
## 3. Create a Project in Github where you want keep your a code and Jenkins will pull code from here
## 4. Create a Free Style Project in Jenkins
  - In General Section check github project and Enter the URL of Repo.
  - In Source Code Management section select git and repository URL that ends with **.git** if you are using private repo give ssh URL and select ssh credentials and select the branch you want to track.
  - In Build trigger section select **github hook trigger for GITScm Polling
  - In build section first execute the scanner [click here]() to checkout how its done
  - Next, Build your project
  - Next, push the built artifact to nexus repository, [click here] to know how to do that.
