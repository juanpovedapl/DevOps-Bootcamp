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
### Validate TaaS Jenkins access
### Cluster creation

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
