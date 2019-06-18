# AppOps-Training

## Welcome

## Contents
- [Pre-requisites](#Pre-requisites)
  * [Github](#Github)
  * [TaaS Artifactory](#Validate-TaaS-Artifactory-access)
  * [Cluster Creation](#Validate-TaaS-Jenkins-access)
  * [Configuring IBM Cloud Private CLI](#Configuring-IBM-Cloud-Private-CLI)
- Hands-On: BDD
- Hands-On: DSAT
- Hands-On: CloudFoundry Weather Application

## Pre requisites

### Github

#### Install git on your machine

1. For Linux, run the following:

```.term1
sudo yum install git
```
Accept the total packages to be downloaded and installed with "y"

2. Confirm your installation:

```.term1
git --version
```

For other OS, check the link [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

#### Check your keys in github enterprise

1. Go to [IBM Github Enterprise](https://github.ibm.com/)

2. Click on your profile photo, and go to "Settings", and then click on "SSH and GPG keys":

![Check git keys](/resources/img/Check_git_keys.gif)

If you have added before your keys before, your going to see something as in the gif.
If you don't see any key, follow the instructions in [here](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account) to add a new key.

#### Clone this repository in your machine

1. Click on "Clone or download"
2. Ensure to clone with SSH and copy the text provided.

![Clone repo](/resources/img/Clone_repo.gif)

3. Open a terminal and move to a folder where you want to store the repository, and enter the following:

```.term1
git clone git@github.ibm.com:AppOpsOrg/AppOps-Training.git
```

Pro-tip: If you don't feel confident using git in the terminal, you can check and practice with this [cheat-sheet](https://www.git-tower.com/blog/git-cheat-sheet).


### Validate TaaS Artifactory access
Artifactory is a universal Artifact Repository Manager, intergrating with CI/CD and DevOps tools to track your artifacts through the development process. As well as offering generic artifact storage, Artifactory offers bespoke and tool-integrated support for the most popular packages including Maven, Docker, NPM, Helm, PyPI, Gradle, Ivy, Debian and RPM.
TaaS offers Artifactory Enterprise in two high availability clusters, NA (Dallas) and EU (London). When onboarding to Artifactory, teams should select their primary cluster closest to their build infrastructure - the repository contents will be automatically replicated to the other cluster. This replica is provided for disaster recovery, and as an alternative (read only) download location.
We will use this repository to store all images created during BDD exercise. Validate your access to Docker Repository [gbs-appops-training-docker-local.artifactory.swg-devops.com](https://na.artifactory.swg-devops.com/artifactory/webapp/#/artifacts/browse/tree/General/gbs-appops-training-docker-local).
### Validate TaaS Jenkins access
Jenkins is a continuous integration and continuous delivery application. By continuously building and testing software projects with Jenkins, it becomes easier for developers to integrate changes in a project and to find and solve defects more rapidly, thereby increasing your productivity.
We will execute our pipeline on Jenkins as a Service offered by IBM. Use your w3 credentials to login into  https://gbs-appops-training-jenkins.swg-devops.com

### Cluster creation

1. Go to [IBM Cloud](https://cloud.ibm.com/login) and log in with your w3 credentials.
2. Once logged in, it will be displayed  the dashboard of your profile, go to the left menu and click on **Kubernetes**.
3. Now click **Create a cluster**.
4. Select **Free** plan.  Set Geography as **North America** and Metro as **Dallas**
5. Write down the cluster name and click **Create cluster**.
6. The cluster has been requested, it will take some minutes to be configure and ready to use. Status will change to green (normal) when it is ready to be used.
![](resources/img/cluster.gif)

### Installing IBM Cloud Private CLI

1. Login to https://bldbzt1160.bld.dst.ibm.com:8443/

2. Go to the left-menu and select "Command Line Tools" and then "Cloud Private CLI"

3. Open the menu "Install IBM Cloud Private CLI" and select your OS, copy the download command.

![InstallationCommand](/resources/img/getInstallationCommand-ICPCLI.gif)

4. Open a terminal and run the command

5. Once downloaded, change the permissions of the file:

```.term1
chmod 755 <file>
```

And then move it:

```.term1
sudo mv <file> /usr/local/bin/cloudctl
```

6. Confirm that the IBM Cloud Private CLI is installed:

```.term1
cloudctl --help
```

7. To login to ICP cluster, run the following:

```.term1
cloudctl login -a https://bldbzt1160.bld.dst.ibm.com:8443/ --skip-ssl-validation
```
