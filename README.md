# AppOps-Training

## Welcome

## Contents
- [Pre-requisites](#Pre-requisites)
  * [1. Installing IBM Cloud Tools](#1-Installing-IBM-Cloud-Tools)
  * [2. Installing Docker](#2-Installing-docker-RHEL)
  * [3. Installing Docker Compose](#3-Installing-Docker-Compose)
  * [4. Github](#4-Github)
  * [5. TaaS Artifactory](#5-Validate-TaaS-Artifactory-access)
  * [6. TaaS Jenkins](#6-Validate-TaaS-Jenkins-access)
  * [7. IBM Cloud Kubernetes Cluster creation](#7-IBM-Cloud-Kubernetes-Cluster-creation)
  * [8. Create an IBM Cloud APIKEY](#8-Create-an-IBM-Cloud-APIKEY)
  * [9. Connecting to IBM Cloud KS cluster](#9-Connecting-to-IBM-Cloud-KS-cluster)
  * [10. Installing IBM Cloud Private CLI](#10-Installing-IBM-Cloud-Private-CLI)
  * [11. SonarQube project creation](#11-SonarQube-project-creation)



- Hands-On: BDD
- Hands-On: DSAT
- Hands-On: CloudFoundry Weather Application

## Pre requisites

### 1. Installing IBM Cloud tools

1. For Mac and Linux, run the following command:
```
curl -sL http://ibm.biz/idt-installer | bash
```  
For Windows 10 Pro, run the following command:
```
[Net.ServicePointManager]::SecurityProtocol = "Tls12"; iex(New-Object Net.WebClient).DownloadString('https://ibm.biz/idt-win-installer')
```  
2. Verify the installation
```
ibmcloud dev help
```  

More info [here](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started)


### 2. Installing Docker RHEL

Docker is included and installed in the previous step, however it does not work for RHEL, if you're working with RHEL follow the next steps:

1. Install required packages
```
sudo yum install -y yum-utils \
device-mapper-persistent-data \
lvm2
```

2. Add **stable** repository
```
sudo yum-config-manager \
--add-repo \
https://download.docker.com/linux/centos/docker-ce.repo
```

3. Install Docker
```
sudo yum install docker-ce docker-ce-cli containerd.io
```

More info [here](https://docs.docker.com/install/linux/docker-ce/centos/)

### 3. Installing Docker Compose

For RHEL workstations, follow the next steps:

1. Run this command to download the current stable release of Docker Compose:

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

2. Apply executable permissions to the binary:
```
sudo chmod +x /usr/local/bin/docker-compose
```

3. Test the installation:
```
docker-compose --version
```

For other OS or troubleshooting check the link [here](https://docs.docker.com/compose/install/).

### 4. Github
Similar to docker, git is installed within IBM Cloud Tools, just verify your installation running:

```.term1
git --version
```

#### Check your keys in github enterprise

1. Log in to [IBM Github Enterprise](https://github.ibm.com/)

2. Click on your profile photo, and go to "Settings", and then click on "SSH and GPG keys":

![Check git keys](resources/img/Check_git_keys.gif)

If you have added your keys before, your going to see something as in the gif.
If you don't see any key, follow the instructions in [here](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account) to add a new key.

#### Fork this repository and clone your forked repository in your machine

1. Fork this repository, as shown below:

![Fork](resources/img/fork_repository.jpg)

2. Once forked, clone your repository in your machine. Ensure to clone with SSH and copy the text provided.

![Clone repo](resources/img/Clone_repo.gif)

3. Open a terminal and move to a folder where you want to store the repository, and enter the following:

```.term1
git clone <your-repository-ssh-key>
```

Pro-tip: If you don't feel confident using git in the terminal, you can check and practice with this [cheat-sheet](https://www.git-tower.com/blog/git-cheat-sheet).


### 5. Validate TaaS Artifactory access
Artifactory is a universal Artifact Repository Manager, intergrating with CI/CD and DevOps tools to track your artifacts through the development process. As well as offering generic artifact storage, Artifactory offers bespoke and tool-integrated support for the most popular packages including Maven, Docker, NPM, Helm, PyPI, Gradle, Ivy, Debian and RPM.  
TaaS offers Artifactory Enterprise in two high availability clusters, NA (Dallas) and EU (London). When onboarding to Artifactory, teams should select their primary cluster closest to their build infrastructure - the repository contents will be automatically replicated to the other cluster. This replica is provided for disaster recovery, and as an alternative (read only) download location.  
We will use this repository to store all images created during BDD and DSAT exercise.
Validate your access to Docker Repository. Execute the following commmand and enter with your w3 credentials:
```
docker login gbs-appops-training-docker-local.artifactory.swg-devops.com
```
You should obtain **Login Succeeded**.

### 6. Validate TaaS Jenkins access
Jenkins is a continuous integration and continuous delivery application. By continuously building and testing software projects with Jenkins, it becomes easier for developers to integrate changes in a project and to find and solve defects more rapidly, thereby increasing your productivity.
We will execute our pipeline on Jenkins as a Service offered by IBM. Use your w3 credentials to login into  https://gbs-appops-training-jenkins.swg-devops.com

### 7. IBM Cloud Kubernetes Cluster creation

1. Go to [IBM Cloud](https://cloud.ibm.com/login) and log in with your w3 credentials.
2. Once logged in, it will be displayed  the dashboard of your profile, go to the left menu and click on **Kubernetes**.
3. Now click **Create a cluster**.
4. Select **Free** plan.  Set Geography as **North America** and Metro as **Dallas**
5. Write down the cluster name and click **Create cluster**.
6. The cluster has been requested, it will take some minutes to be configure and ready to use. Status will change to green (normal) when it is ready to be used.
![](resources/img/cluster.gif)

### 8. Create an IBM Cloud APIKEY
As an IBM Cloud user you might want to use an API key when you enable a program or script without distributing your password to the script. A benefit of using an API key can be that a user or organization can create several API Keys for different programs and the API keys can be deleted independently if compromised without interfering with other API keys or even the user.
To create an API key for your user identity in the UI, complete the following steps:
1. Go to **Manage > Access(IAM) > IBM Cloud API Keys.**
2. Click **Create an IBM Cloud API key.**
3. Enter a name and description for your API key.
4. Click **Create.**
5. Then, click **Show** to display the API key. Or, click **Copy** to copy and save it for later, or click **Download.**

![](resources/img/apikey.gif)

### 9. Connecting to IBM Cloud KS cluster

1. Log in to your IBM Cloud account. We will use our API key to login into our cluster.
```
ibmcloud login -apikey <YOUR_APIKEY>  -r us-south -g default
```
2. Download the kubeconfig files for your cluster.
```
ibmcloud ks cluster-config --cluster <YOUR_CLUSTER>
```
3. Using the output from the previous step, set the KUBECONFIG environment variable. For example:
```
export KUBECONFIG=/home/$USER/.bluemix/plugins/container-service/clusters/mycluster/kube-config-hou02-mycluster.yml
```
4. Verify kubectl can communicate with your cluster.
```
kubectl cluster-info
```

### 10. Installing IBM Cloud Private CLI

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

### 11. SonarQube project creation

1. Validate your access to SonarQube:
[SonarQube](http://wdcdmzyz22033184.ibmcloud.dst.ibm.com/about)

2. Login with the following credentials:

**User:** w3-ID

**Password:** w3-ID

3. Once logged, create your project:

- Go to "+" sign, in the up-right corner

- Click on "Create new project"

 **Project Key:** w3-ID-DSAT

 **Display Name:** w3-ID-DSAT

 - Click "Set Up". It will get you to a different screen called "Analyze your project"

 - Create a token clicking in "Generate", save this token somewhere you remember (we will use it later in DSAT exercise).

 - In the section "Run analysis on your project", select "Other (JS..."

 - You're now ready to work with sonarQ.

![SonarQ project](/resources/img/SonarQ_project-creation.gif)

 - Check that your project is listed in the Projects tab: http://wdcdmzyz22033184.ibmcloud.dst.ibm.com/projects
